```
density_from_statevector(ψ::Vector)
```

量子状態 `ψ` に対応する密度行列 |ψ⟩⟨ψ| (パウリ表現) を構築します。

```jldoctest
julia> ψ = 1/sqrt(2)[1, -1]; # ケットを作成 - 状態。
julia> ρ = density_from_statevector(ψ)
DensityMatrix([0.9999999999999998, -0.9999999999999998, 0.0, 0.0], 1)
```
