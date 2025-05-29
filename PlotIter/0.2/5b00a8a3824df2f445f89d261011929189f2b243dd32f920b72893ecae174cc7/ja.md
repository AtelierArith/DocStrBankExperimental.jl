```
plot_iter(f::Function, iterable; kwargs...)
```

`iterable`の各アイテムごとに1つのプロットを生成します。

この関数は、`iterable`内の各アイテムに対して`f`を呼び出し、新しいプロットを`Plots.current()`として設定します。

これはJupyterノートブック内での使用に最適化されています。利用可能なページ幅を活用して、迅速に多数のプロットを生成できます。プロットは互いに近接しているため、視覚的に比較しやすくなります。

この関数は、この単純なケースのために手動でレイアウトを構築する必要を回避します。

# 引数

  * `f::Function`: 型`eltype(iterable)`の単一引数を取る関数。返り値は無視されます。
  * `iterable`: 任意のイテラブルオブジェクト。

# キーワード引数

  * `num_cols::Integer=3`: 横に並べるプロットの数。
  * `row_width=900`: 各行の幅（すべてのプロットのための幅）
  * `row_height=300`: 各プロットの垂直の広がり。
  * `display_mode::DisplayMode=DisplayAtEnd()`: インスタンス：

      * [`NoDisplay`](@ref): プロットを`show`しない。
      * [`DisplayEachRow`](@ref): プロットの行が完成するたびに`show`する。
      * [`DisplayAtEnd`](@ref): すべてのプロットが生成されるまで待ち、一度にすべてを表示する。
  * `xlims_convex_hull::Bool=false`: trueの場合、すべてのプロットに対して[`xlims_convex_hull!`](@ref)を呼び出します。これは`display_mode`が[`NoDisplay`](@ref)または[`DisplayAtEnd`](@ref)である必要があります。
  * `ylims_convex_hull::Bool=false`: trueの場合、すべてのプロットに対して[`ylims_convex_hull!`](@ref)を呼び出します。これは`display_mode`が[`NoDisplay`](@ref)または[`DisplayAtEnd`](@ref)である必要があります。
  * `zlims_convex_hull::Bool=false`: trueの場合、すべてのプロットに対して[`zlims_convex_hull!`](@ref)を呼び出します。これは`display_mode`が[`NoDisplay`](@ref)または[`DisplayAtEnd`](@ref)である必要があります。
  * `clims_convex_hull::Bool=false`: trueの場合、すべてのプロットに対して[`clims_convex_hull!`](@ref)を呼び出します。これは`display_mode`が[`NoDisplay`](@ref)または[`DisplayAtEnd`](@ref)である必要があります。
  * `kwargs...`: 指定された他のキーワード引数は、最初の`plot`呼び出しに転送されます。

# 戻り値

生成されたすべてのプロットのベクター。

# 例

設定なしでの最も簡単な使用法は次のとおりです：

```julia
plot_iter(1:3) do i
    # 注意: `plot`ではなく`plot!`を呼び出すことが重要です。なぜなら、`plot_iter`によって
    # すでに新しいプロットオブジェクトが作成されているからです。
    plot!(i .* rand(30))
end;
```

サイズを変更したり、y軸の制限を一致させたりすることもできます：

```julia
plot_iter(1:3; num_cols=2, row_height=500, ylims_convex_hull=true) do i
    plot!(i .* rand(30))
end;
```
