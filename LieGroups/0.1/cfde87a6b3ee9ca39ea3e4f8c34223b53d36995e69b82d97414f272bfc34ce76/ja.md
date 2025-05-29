```
InverseLeftGroupOperationAction <: AbstractRightGroupActionType
```

グループ自体に作用する際の[`AbstractLeftGroupActionType`](@ref)の型であり、[`LeftGroupOperationAction`](@ref) $σ_h$の逆によって与えられます。

$$
τ_h(g) \coloneqq σ_h^{-1}(g) = σ(h^{-1},g) = h^{-1}∘g
$$

名前においては左作用の逆であることに注意してくださいが、その性質はそれが[`AbstractRightGroupActionType`](@ref)であることを示しています。なぜなら、

$$
τ_g(τ_h(p))
= σ^{\mathrm{L}}_{g^{-1}}(σ^{\mathrm{L}}_{h^{-1}}(p))
= σ^{\mathrm{L}}_{g^{-1}h^{-1}}(p)
= σ^{\mathrm{L}}_{(hg)^{-1}}(p)
τ_{hg}(p).
$$

その逆$(σ_h)^{-1}$については[`InverseLeftGroupOperationAction`](@ref)を参照してください。

!!! note
    一部の文献では、これ自体を*右群作用*と呼ぶこともあります。

