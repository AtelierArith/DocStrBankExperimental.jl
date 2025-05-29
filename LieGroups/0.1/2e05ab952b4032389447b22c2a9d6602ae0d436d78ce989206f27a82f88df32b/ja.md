```
AbstractRightGroupActionType <: AbstractGroupActionType
```

[`AbstractLieGroup`](@ref) $\mathcal G$ が（右から）[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$ に作用する（滑らかな）群作用 $σ: \mathcal M × \mathcal G → \mathcal M$ を表す型です。以下の性質を持ちます。

1. $$
    σ(p, \mathrm{e}) = p
    $$

    はすべての $p ∈ \mathcal M$ に対して成り立ちます。
2. $$
    σ(σ(p, g), h) = σ(p, g∘h)
    $$

    はすべての $g,h ∈ \mathcal G$, $p ∈ \mathcal M$ に対して成り立ちます。

ここで、$∘$ は [`AbstractLieGroup`](@ref) $\mathcal G$ の群演算を示します。詳細は [HilgertNeeb:2012; Remark 9.1.12](@cite) を参照してください。

作用の型は、作用を家族 $σ_g(p)$ として書くと少しわかりやすくなります。第二の性質から次のように得られます。

$$
  σ_g(σ_h(p)) = σ_{hg}(p)
$$

ここで $g$ が右側に現れることがわかります。

群演算がどの側から作用しているかを強調するために、時々 $σ^{\mathrm{R}}$ と書きます。文脈から作用が明らかな場合、$σ(p, g) = p ⋅ g$ と書きます。

右作用の顕著な例は、[`AbstractLeftGroupActionType`](@ref) $σ^{\mathrm{L}}$ の作用の逆であり、次のように与えられます：$τ_g = (σ^{\mathrm{L}}_g)^{-1} = σ^{\mathrm{L}}_{g^{-1}}$。次のように得られます。

$$
τ_g(τ_h(p))
= σ^{\mathrm{L}}_{g^{-1}}(σ^{\mathrm{L}}_{h^{-1}}(p))
= σ^{\mathrm{L}}_{g^{-1}h^{-1}}(p)
= σ^{\mathrm{L}}_{(hg)^{-1}}(p)
τ_{hg}(p).
$$

!!! note
    関数定義では、作用の家族のアイデアに従い、関数シグネチャでは順序 `(M, g, p)` を使用します。

