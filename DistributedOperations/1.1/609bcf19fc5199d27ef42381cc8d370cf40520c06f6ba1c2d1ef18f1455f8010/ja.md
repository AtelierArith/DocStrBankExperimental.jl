```
y = reduce!(x::TypeFutures[, reducemethod!=DistributedOperations.paralleloperations_reduce!])
```

`x::TypeFutures`の並列還元を`reducemethod!`を使用して行います。デフォルトでは、還元はミューテーションのインプレース要素ごとの加算であり、`y=localpart(x)`となります。

# 例

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
x = ArrayFutures(Float64, (3,))
fill!(x, 1, workers())
y = reduce!(x)
y ≈ [2.0,2.0,2.0] # true
localpart(x) ≈ [2.0,2.0,2.0] # true
rmprocs(workers())
```
