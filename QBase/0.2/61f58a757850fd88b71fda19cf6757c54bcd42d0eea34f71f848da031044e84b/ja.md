```
mutual_information(
    priors :: AbstractVector,
    ρ_states :: Vector{<:AbstractMatrix},
    Π :: AbstractVector
) :: Float64
```

量子状態と測定のエンコーディングおよびデコーディングに対する古典的な相互情報量を計算します。条件付き確率は、[`measure`](@ref)を使用して量子状態と測定から取得されます。

次の場合に`DomainError`がスローされます：

  * `priors`が[`is_probability_distribution`](@ref)を満たさない場合。
  * 任意の`ρ ∈ ρ_states`が[`is_density_matrix`](@ref)を満たさない場合。
  * `Π`が[`is_povm`](@ref)を満たさない場合。
