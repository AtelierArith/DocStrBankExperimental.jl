```
predict(ARX::TransferFunction, d::InputOutputData)
```

ARXプロセスの1ステップ先予測。返される予測の長さは `length(d) - max(na, nb)`

# 例:

```jldoctest
julia> predict(tf(1, [1, -1], 1), iddata(1:10, 1:10))
9-element Vector{Int64}:
  2
  4
  6
  8
 10
 12
 14
 16
 18
```
