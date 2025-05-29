```
AbstractUncertainIndexValueDataset
```

A dataset of uncertain value (`UncertainValue` instances), with indices (time, depth, etc..) that are also uncertain values (`UncertainValue` instances).

Concrete types must as a minimum implement the following fields:

  * **`indices::UncertainDataset`**: The (uncertain) indices of the dataset.
  * **`values::UncertainDataset`**: The (uncertain) values of the dataset.
