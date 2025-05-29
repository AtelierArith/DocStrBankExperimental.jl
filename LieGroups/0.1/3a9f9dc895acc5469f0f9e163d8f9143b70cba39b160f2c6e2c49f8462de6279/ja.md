```
LeftSemidirectProductLieGroup(
    N::LieGroup, H::LieGroup, action::AbstractGroupActionType=default_left_action(N, H)
)
```

セミダイレクト積リー群 $\mathcal G = N ⋉ H$ を生成します。これは [`AbstractLeftGroupActionType`](@ref) を使用し、群演算の定義には [`LeftSemidirectProductGroupOperation`](@ref) を、詳細については [HilgertNeeb:2012; Definition 9.2.22](@cite) の第二の定義を参照してください。

短縮形 `N`[`⋉`](@ref ⋉(L1::LieGroup, L2::LieGroup))`H` は、対応する [`default_left_action`](@ref)`(N,H)` が使用したいものである場合に使用できます。
