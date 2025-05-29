```
vol(::SecondOrderTensor)
```

二次テンソルの体積部分を加法分解に基づいて計算します。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2,3})
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> vol(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.538159  0.0       0.0
 0.0       0.538159  0.0
 0.0       0.0       0.538159

julia> vol(A) + dev(A) ≈ A
true
```
