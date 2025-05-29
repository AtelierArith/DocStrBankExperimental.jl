```
pairplot(gridpos::Makie.GridLayout, inputs...; kwargs...)
```

便利な関数で、完全に指定されていない1つ以上の入力に対して合理的なペアプロットを作成します。入力テーブルをPairPlots.Series()でラップし、各系列に指定された異なる色を使用します。

単一のデータテーブルに適用されるデフォルトは次のとおりです：

```julia
pairplot(fig[1,1], table) == # おおよそ以下のようになります：
pairplot(
    PairPlots.Series(table, color=Makie.RGBA(0., 0., 0., 0.5)) => (
        PairPlots.HexBin(colormap=Makie.cgrad([:transparent, :black]),),
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contour(),
        PairPlots.MarginDensity(
            color=:transparent,
            color=:black,
            linewidth=1.5f0
        ),
        PairPlots.MarginQuantileText()
    )
)
```

2つから5つのデータテーブルに適用されるデフォルトは次のとおりです：

```julia
pairplot(fig[1,1], table1, table2) == # おおよそ以下のようになります：
pairplot(
    PairPlots.Series(table1, color=Makie.wong_colors(0.5)[1]) => (
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contourf(),
        PairPlots.MarginDensity(
            linewidth=2.5f0
        )
    ),
    PairPlots.Series(table2, color=Makie.wong_colors(0.5)[2]) => (
        PairPlots.Scatter(filtersigma=2),
        PairPlots.Contourf(),
        PairPlots.MarginDensity(
            linewidth=2.5f0
        )
    ),
)
```

6つ以上のテーブルの場合、デフォルトはおおよそ次のようになります：

```julia
PairPlots.Series(table1, color=Makie.wong_colors(0.5)[series_i]) => (
    PairPlots.Contour(sigmas=[1]),
    PairPlots.MarginDensity(
        linewidth=2.5f0
    )
)
```
