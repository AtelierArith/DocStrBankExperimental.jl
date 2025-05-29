```
ridgeplot(x::Union{MixedModel,MixedModelBootstrap}; kwargs...)::Figure
ridgeplot!(fig::Union{GridLayoutBase.GridLayout, GridLayoutBase.GridPosition, GridLayoutBase.GridSubposition, Makie.Figure}, x::Union{MixedModel,MixedModelBootstrap};
          kwargs...)
ridgeplot!(ax::Axis, Union{MixedModel,MixedModelBootstrap};
          conf_level=0.95, vline_at_zero=true, show_intercept=true,
          scatter_attributes=(;),
          errorbars_attributes=(;),
          band_attributes=(;),
          lines_attributes=(;),
          attributes...)
```

ブートストラップサンプルの固定効果のためのリッジプロットを作成します。

密度は最大密度が常に1になるように正規化されます。

`conf_level`に対応する最高密度区間は、各密度の下部にバーでマークされます。`conf_level=missing`を設定すると、最高密度区間のマークが削除されます。

`attributes`は[`coefplot`](@ref)、`band!`および`lines!`に渡されます。`scatter_attributes`および`errorbars_attributes`は[`coefplot`](@ref)にのみ渡されます。`band_attributes`および`lines_attributes`はそれぞれ`band!`および`linesbars!`にのみ渡されます。（Makie 0.21以降、特定のプロットタイプに対してサポートされていない属性は静かに無視されなくなったため、単一のプロットタイプにのみ有効な属性を分ける必要があります。）

変更するメソッドは元のオブジェクトを返します。

!!! note
    推定不可能な係数（ランク欠陥の場合にピボットによって削除された係数）は除外されます。

