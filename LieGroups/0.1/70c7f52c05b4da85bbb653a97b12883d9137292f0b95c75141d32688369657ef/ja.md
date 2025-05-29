```
InverseRightGroupOperationAction <: AbstractLeftGroupActionType
```

グループ自体に作用する [`AbstractLeftGroupActionType`](@ref) の型であり、これは [`RightGroupOperationAction`](@ref) $σ_h$ の逆によって与えられます。

$$
τ_h(g) \coloneqq σ_h^{-1}(g) = σ(h^{-1},g) = g∘h^{-1}
$$

名前においては右作用の逆であることに注意してくださいが、その性質はそれが [`AbstractLeftGroupActionType`](@ref) であることを示しています。なぜなら、

$$
τ_g(τ_h(p))
= σ^{\mathrm{R}}_{g^{-1}}(σ^{\mathrm{R}}_{h^{-1}}(p))
= σ^{\mathrm{R}}_{h^{-1}g^{-1}}(p)
= σ^{\mathrm{R}}_{(gh)^{-1}}(p)
τ_{gh}(p).
$$

その逆 $(σ_h)^{-1}$ については [`InverseLeftGroupOperationAction`](@ref) を参照してください。
