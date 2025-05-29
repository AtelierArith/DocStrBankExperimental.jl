```
pushinstances!(md, instance)
```

Add an instance to a multimodal dataset, and return the dataset itself.

The instance can be a `DataFrameRow` or an `AbstractVector` but in both cases the number and type of variables should match those of the dataset.
