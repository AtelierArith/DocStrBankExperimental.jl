```
GroupAction{T<:GroupActionType, L<:LieGroup, M<:AbstractManifold}
```

[`AbstractGroupActionType`](@ref) `T` のグループアクションを指定し、[`AbstractLieGroup`](@ref) `G` が `M` に作用します。

$$
\mathcal M
$$

を [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) とし、$\mathcal G$ をグループ演算 $∘$ を持つ [`AbstractLieGroup`](@ref) とします。

グループ $\mathcal G$ の（滑らかな）アクションは、次のような写像です。

$$
σ: \mathcal G × \mathcal M → \mathcal M
$$

その性質は次の通りです。

  * $$
    σ(\mathrm{e}, p) = p
    $$

    はすべての $p ∈ \mathcal M$ に対して成り立ちます。
  * $$
    σ(g, σ(h, p)) = σ(g∘h, p)
    $$

    はすべての $g,h ∈ \mathcal G$, $p ∈ \mathcal M$ に対して成り立ちます。

# フィールド

  * `type::T`: グループアクションの型。
  * `group::L`: 作用するグループ。
  * `manifold::M`: グループが作用する多様体。

詳細については [HilgertNeeb:2012; Section 9.1.3](@cite) を参照してください。
