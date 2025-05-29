```
holevo_bound(
    priors :: AbstractVector,
    ρ_states :: Vector{<:AbstractMatrix}
) :: Float64
```

ホレーボの定理は、[`mutual_information`](@ref) $I(X : Y) \leq \mathcal{X}$ に対して上限を置きます。これは、一連の量子状態からデコードできる情報の量に制限を設けます。混合状態 $\rho = \sum_i p_i \rho_i$ に対して、ホレーボの上限 $\mathcal{X}$ は次のように定義されます。

$$
\mathcal{X}  := S(\rho) - \sum_i p_i S(\rho_i)
$$

ここで、$S(\rho)$ は [`von_neumann_entropy`](@ref) です。

次の場合に `DomainError` がスローされます：

  * `priors` が [`is_probability_distribution`](@ref) を満たさない場合。
  * いずれかの `ρ ∈ ρ_states` が [`is_density_matrix`](@ref) を満たさない場合。
