```
RightSemidirectProductLieGroup(
    N::LieGroup, H::LieGroup, action::AbstractGroupActionType=default_right_action(N,H)
)
```

セミダイレクト積リー群 $\mathcal G = N ⋊ H$ を生成します。これは [`AbstractLeftGroupActionType`](@ref) を使用し、グループ演算の定義には [`RightSemidirectProductGroupOperation`](@ref) を、さらに詳細については [HilgertNeeb:2012; Definition 9.2.22](@cite) の最初の定義を参照してください。

短縮形 `N`[`⋊`](@ref ⋊(L1::LieGroup, L2::LieGroup))`H` は、対応する [`default_right_action`](@ref)`(N,H)` が使用したいものである場合に使用できます。
