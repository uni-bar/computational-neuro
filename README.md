# computational-neuro

For best performance, use the dataset on [hugginface](https://huggingface.co/datasets/bareket/larva)

it can be used like this:
```python
from datasets import load_dataset

# Load the dataset from the Hub.
# Replace "Bareket/larva" with your actual repository name if different.
dataset = load_dataset("Bareket/larva", split="train")

# Inspect the dataset.
print(dataset)
print("First sample:", dataset[0])

from collections import Counter
import pandas as pd

print("Dataset Features:")
print(dataset.features)
print("\n")

# Print the label names (folder names).
if "label" in dataset.features:
    label_names = dataset.features["label"].names
    print("Label names:", label_names)
else:
    print("No 'label' field found in the dataset features.")

# Count the number of images for each label.
# Using collections.Counter
labels = dataset["label"]  # This is a list of integer labels.
label_counts = Counter(labels)
print("\nLabel counts (using Counter):")
for label_id, count in label_counts.items():
    # Convert the numeric label to its corresponding folder name.
    folder_name = label_names[label_id] if "label" in dataset.features else str(label_id)
    print(f"{folder_name}: {count}")
```
