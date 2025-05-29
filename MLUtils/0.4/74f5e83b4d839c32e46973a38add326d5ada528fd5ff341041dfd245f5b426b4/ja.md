```
batchsize(data::BatchView) -> Int
```

`data`の各バッチの固定サイズを返します。

# 例

```julia
using MLUtils
X, Y = MLUtils.load_iris()

A = BatchView(X, batchsize=30)
@assert batchsize(A) == 30
```
