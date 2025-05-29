```
density_from_matrix(ρmat::AbstractMatrix)
```

行列 `ρmat` からパウリ表現の密度行列を構築します。

```jldoctest
julia> ρmat = 0.15 .*[ 1 -1; -1  1] + 0.35 .* [1 1; 1 1]; # + と - の混合状態を作成します。
julia> ρ = density_from_matrix(ρmat)
DensityMatrix([1.0, 0.39999999999999997, 0.0, 0.0], 1)
```
