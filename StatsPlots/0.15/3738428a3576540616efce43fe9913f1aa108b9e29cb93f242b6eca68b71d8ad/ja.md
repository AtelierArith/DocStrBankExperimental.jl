```
andrewsplot(args...; kw...)
```

配列（またはテーブル）の各行を線として表示します。`x` 引数はグループ化変数を指定します。これは高次元データの構造を視覚化する方法です。 https://en.wikipedia.org/wiki/Andrews_plot #Examples

```julia
using RDatasets, StatsPlots
iris = dataset("datasets", "iris")
@df iris andrewsplot(:Species, cols(1:4))
```
