hpd_heatmap(histogram, probabilities, colors)

ヒストグラムから `ColorMatrix` を生成し、指定された色でさまざまな確率密度領域を強調表示します。

`probabilities` は増加している必要があり、`0` と `1` の間で、要素は `color` よりも小さい必要があります。両方とも反復可能であることができます。

!!! note
    メソッドは、パッケージ `StatsBase` がロードされているときのみ定義されています。

