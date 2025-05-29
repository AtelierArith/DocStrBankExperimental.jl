```
AbstractLeftGroupActionType <: AbstractGroupActionType
```

[`AbstractLieGroup`](@ref) $\mathcal G$ が [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$ に（左から）作用する（滑らかな）群作用 $σ: \mathcal G × \mathcal M → \mathcal M$ を表す型です。以下の性質を持ちます。

1. $$
    σ(\mathrm{e}, p) = p
    $$

    はすべての $p ∈ \mathcal M$ に対して成り立ちます。
2. $$
    σ(g, σ(h, p)) = σ(g∘h, p)
    $$

    はすべての $g,h ∈ \mathcal G$, $p ∈ \mathcal M$ に対して成り立ちます。

ここで、$∘$ は [`AbstractLieGroup`](@ref) $\mathcal G$ の群演算を示します。詳細は [HilgertNeeb:2012; Definition 9.1.11](@cite) を参照してください。

作用の型は、作用を家族 $σ_g(p)$ として書くことで少し明確に見ることができます。第二の性質から次のように得られます。

$$
  σ_g(σ_h(p)) = σ_{gh}(p)
$$

そして $g$ が左側に現れることがわかります。

群演算がどの側から作用しているかを強調するために、時々 $σ^{\mathrm{L}}$ と書きます。文脈から作用が明らかな場合は、$σ(g, p) = g ⋅ p$ と書きます。

左作用の顕著な例は、[`AbstractRightGroupActionType`](@ref) $σ^{\mathrm{R}}$ の作用の逆であり、次のように与えられます：$τ_g = (σ^{\mathrm{R}}_g)^{-1} = σ^{\mathrm{R}}_{g^{-1}}$。次のように得られます。

$$
τ_g(τ_h(p))
= σ^{\mathrm{R}}_{g^{-1}}(σ^{\mathrm{R}}_{h^{-1}}(p))
= σ^{\mathrm{R}}_{h^{-1}g^{-1}}(p)
= σ^{\mathrm{R}}_{(gh)^{-1}}(p)
τ_{gh}(p).
$$

!!! note
    関数定義では、作用の家族のアイデアに従い、関数シグネチャでは順序 `(M, g, p)` を使用します。

