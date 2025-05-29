```
coefplot(x::Union{MixedModel,MixedModelBootstrap}; kwargs...)::Figure
coefplot!(fig::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, x::Union{MixedModel,MixedModelBootstrap};
          kwargs...)
coefplot!(ax::Axis, Union{MixedModel,MixedModelBootstrap};
          conf_level=0.95, vline_at_zero=true, show_intercept=true,
          scatter_attributes=(;),
          errorbars_attributes=(;),
          attributes...)
```

固定効果と関連する信頼区間の係数プロットを作成します。

推定不可能な係数（ランク欠陥の場合にピボットによって削除された係数）は除外されます。

`attributes` は `scatter!` と `errorbars!` の両方に渡され、`scatter_attributes` と `errorbars_attributes` はそれぞれ `scatter!` と `errorbars!` のみに渡されます。（Makie 0.21以降、特定のプロットタイプに対してサポートされていない属性は静かに無視されなくなったため、単一のプロットタイプに対してのみ有効な属性を分ける必要があります。）

変更するメソッドは元のオブジェクトを返します。

!!! note
    推定不可能な係数（ランク欠陥の場合にピボットによって削除された係数）は除外されます。

