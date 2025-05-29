```
otimesu(::SecondOrderTensor, ::SecondOrderTensor)
```

2つのテンソル間の「上」オープン積を計算します。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> B = rand(SymmetricTensor{2, 2});

julia> otimesu(A, B)
2×2×2×2 Tensor{4, 2, Float64, 16}:
[:, :, 1, 1] =
 0.291503  0.115106
 0.490986  0.193876

[:, :, 2, 1] =
 0.490986  0.193876
 0.19547   0.0771855

[:, :, 1, 2] =
 0.115106  0.128518
 0.193876  0.216466

[:, :, 2, 2] =
 0.193876   0.216466
 0.0771855  0.086179
```
