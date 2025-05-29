```
symrcm(matrix[, alg::Algorithm])
```

逆カッシル・マッキーアルゴリズムを使用して、行列の帯域幅を減少させます。

# 例

```julia
julia> using BandedMatrices, CliqueTrees

julia> matrix = [
           1 0 1 0 0 0 0 1 1
           0 1 1 0 0 1 1 1 0
           1 1 1 0 0 0 0 0 0
           0 0 0 1 0 0 0 1 1
           0 0 0 0 1 0 1 1 0
           0 1 0 0 0 1 1 0 0
           0 1 0 0 1 1 1 0 0
           1 1 0 1 1 0 0 1 0
           1 0 0 1 0 0 0 0 1
       ];

julia> bandedmatrix, perm, invp = symrcm(matrix);

julia> bandedmatrix
9×9 LinearAlgebra.Symmetric{Int64, BandedMatrix{Int64, Matrix{Int64}, Base.OneTo{Int64}}}:
 1  1  1  0  ⋅  ⋅  ⋅  ⋅  ⋅
 1  1  1  1  0  ⋅  ⋅  ⋅  ⋅
 1  1  1  0  1  1  ⋅  ⋅  ⋅
 0  1  0  1  0  1  0  ⋅  ⋅
 ⋅  0  1  0  1  0  1  0  ⋅
 ⋅  ⋅  1  1  0  1  1  1  0
 ⋅  ⋅  ⋅  0  1  1  1  0  1
 ⋅  ⋅  ⋅  ⋅  0  1  0  1  1
 ⋅  ⋅  ⋅  ⋅  ⋅  0  1  1  1

julia> bandedmatrix == matrix[perm, perm]
true
```
