```
concat(dataset1::DimStack, dataset2::DimStack)::DimStack
```

Concatanate two DimStack data sets. If keys are duplicated, dimarrays of dataset1 will be overwritten. `DimArray`s in the concatenated `DimStack` data set are programmatically indistinguishable from those in the original `DimStack` data sets.
