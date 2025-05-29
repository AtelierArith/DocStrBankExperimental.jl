```julia
struct MinMaxSkOp <: CompressiveLearning.BaseSkOp
```

A sketching operators which computes the bounds of the dataset for each dimension.

# Fields

  * `d::Any`:  Dimension of the data
