```
eigen(A::SymmetricTensor{2})
```

対称二次テンソルの固有値と固有ベクトルを計算し、`Eigen`オブジェクトを返します。固有値は`Vec`に格納され、昇順にソートされます。対応する固有ベクトルは`Tensor`の列として格納されます。

[`eigvals`](@ref)および[`eigvecs`](@ref)を参照してください。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> E = eigen(A);

julia> E.values
2-element Vec{2, Float64}:
 -0.27938877799585415
  0.8239521616782797

julia> E.vectors
2×2 Tensor{2, 2, Float64, 4}:
 -0.671814  0.74072
  0.74072   0.671814
```
