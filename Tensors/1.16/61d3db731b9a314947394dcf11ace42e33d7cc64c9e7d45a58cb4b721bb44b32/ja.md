```
det(::SecondOrderTensor)
```

2次テンソルの行列式を計算します。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2,3})
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> det(A)
-0.002539324113350679
```
