```
GeneralizedDataSet(dist::ContinuousMultivariateDistribution, dims::Tuple{Int,Int,Int}=(length(dist), 1, 1))
```

一般的なx-y-共分散を考慮できるデータ構造で、`dims=(Npoints, xdim, ydim)`はデータの次元を示します。`dist`は空間$\mathcal{X}^N \times \mathcal{Y}^N$上で滑らかな分布を構成する必要があり、`mean(dist)`は観測値$(x_1, ..., x_N, y_1, ..., y_N)$の（最も可能性の高い値の）連結として解釈され、`dist`の幅は信号の不確実性を指定します。通常、`dist`は多変量ガウス分布ですが、コーシー分布やスチューデントのt分布など他の分布も可能です。したがって、従属変数$y$と独立変数$x$の間の任意の相関をエンコードできます。

!!! note
    $$
    x
    $$

    と$y$の変数間に相関がない場合（すなわち、`cov(dist)`のオフダイアゴナルブロックがゼロの場合）、与えられたデータをエンコードするために`DataSetExact`型を使用する方がパフォーマンスが向上する可能性があります。

