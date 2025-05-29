```
dot(::SymmetricTensor{2})
```

対称二次テンソルのドット積を自身と計算します。`SymmetricTensor`を返します。

関連情報としては [`tdot`](@ref) と [`dott`](@ref) を参照してください。

# 例

```jldoctest
julia> A = rand(SymmetricTensor{2,3})
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> dot(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.455498  0.74715  0.351309
 0.74715   1.22582  0.575
 0.351309  0.575    0.327905
```
