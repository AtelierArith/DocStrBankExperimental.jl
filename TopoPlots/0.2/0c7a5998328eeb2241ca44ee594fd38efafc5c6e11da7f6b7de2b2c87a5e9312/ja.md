```
eeg_topoplot(data::Vector{<: Real}, labels::Vector{<: AbstractString})
```

属性:

  * `positions::Vector{<: Point} = Makie.automatic`: ラベル（チャネル）名から計算できます。現在、10/20モンタージュのみデフォルト座標が提供されています。
  * `labels::AbstractVector{<:AbstractString} = Makie.automatic`: `label_text`がtrueに設定されている場合、カスタムラベルを追加します。`positions`が指定されていない場合、`labels`は10/20座標を参照するために使用されます。
  * `head = (color=:black, linewidth=3)`: 頭の輪郭を描画します。頭の輪郭を描画しない場合は何も設定せず、そうでない場合は形状を描画する`line!`呼び出しに渡される名前付きタプルを設定します。

# topoplotのいくつかの属性は異なるデフォルトに設定されています:

  * `label_scatter = true`
  * `contours = true`
  * `enlarge = 1`

それ以外の場合、レシピは単に[`topoplot`](@ref)のデフォルトを使用し、属性を通過させます。

!!! 注     10-05チャネルの位置は、https://github.com/sappelhoff/eeg*positions/に基づく「完璧な」球面位置です - mne-defaultの10-20位置は_そうではなく、fsaverageの頭に歪められました。これにより、ここで提供される位置は視覚化には適していますが、ソースの位置特定には適していません。

!!! 注     ラベルを表示するには、`label_text=true`を設定する必要があります。
