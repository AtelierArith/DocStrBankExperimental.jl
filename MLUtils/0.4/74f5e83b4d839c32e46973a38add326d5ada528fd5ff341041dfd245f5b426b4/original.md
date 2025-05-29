```
batchsize(data::BatchView) -> Int
```

Return the fixed size of each batch in `data`.

# Examples

```julia
using MLUtils
X, Y = MLUtils.load_iris()

A = BatchView(X, batchsize=30)
@assert batchsize(A) == 30
```
