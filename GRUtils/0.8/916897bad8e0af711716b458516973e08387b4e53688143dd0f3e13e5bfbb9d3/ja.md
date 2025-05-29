```
histogram(data; kwargs...)
```

`data`のヒストグラムを描画します。

次のキーワード引数を指定できます：

  * `nbins`: ビンの数。デフォルトでは、または1未満の数が指定された場合、ビンの数は`3.3 * log10(n) + 1`として計算されます。ここで、`n`は`data`の要素数です。
  * `horizontal`: ヒストグラムを水平にするかどうか（デフォルトは`false`）。
  * `color`: バーの16進RGBカラーコード。

!!! note
    垂直軸（または`horizontal == true`の場合は水平軸）が対数スケールに設定されている場合、ヒストグラムのバーは1.0から始まります。


# 例

```julia
# サンプルデータを作成
data = 2 .* randn(100) .- 1
# 19ビンでヒストグラムを描画
histogram(data, nbins=19)
# 対数スケールの水平ヒストグラム
histogram(data, horizontal=true, xlog=true)

```
