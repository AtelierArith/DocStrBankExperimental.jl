```
bar(x,y)
bar!(x,y)
```

`y` と `x` のバー プロットを作成します。

# キーワード引数

  * `bar_position::Symbol`: `:overlay` (デフォルト) または `:stack` から選択します。 (警告: 部分的にしか実装されていない可能性があります)。 エイリアス: (:bar_positions, :barpositions)。
  * `bar_width::Real`: データ座標におけるバーの幅。 `nothing` の場合、`x` (または `orientation = :h` の場合は `y`) に基づいて選択されます。 エイリアス: (:bar_widths, :barwidths)。
  * `bar_edges::Bool`: バーをエッジ (true) に揃えるか、中心 (デフォルト) に揃えるか ?。
  * `fillrange::Union{Real, AbstractVector}`: フィルタイプのために `fillrange` と `y` の間の領域を塗りつぶし、`bar`、`sticks` タイプの基準を設定し、他のタイプにも同様に適用します。 エイリアス: (:fill_between, :fillbetween, :fillranges, :fillrng, :fillto, :frange)。
  * `permute::Tuple{Symbol, Symbol}`: タプルで指定された軸のデータと軸のプロパティを入れ替えます。例: (:x, :y)。 エイリアス: (:permutes,)。

# 例

```julia-repl
julia> bar([1,2,3],[4,5,6],fillcolor=[:red,:green,:blue],fillalpha=[0.2,0.4,0.6])
julia> bar([(1,4),(2,5),(3,6)])
```
