```
norm(::Vec)
norm(::SecondOrderTensor)
norm(::FourthOrderTensor)
```

テンソルのノルムを計算します。

# 例

```jldoctest
julia> A = rand(Tensor{2,3})
3×3 Tensor{2, 3, Float64, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> norm(A)
1.8223398556552728
```
