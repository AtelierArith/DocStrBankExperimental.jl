```
PlasmoPlots.layout_plot(
    graph::OptiGraph; 
    node_labels=false, 
    subgraph_colors=false, 
    node_colors=false, 
    linewidth=2.0,
    linealpha=1.0, 
    markersize=30,
    labelsize=20, 
    markercolor=:grey,
    layout_options = Dict(
        :tol => 0.01,
        :C => 2,
        :K => 4, 
        :iterations => 2
    ),
    plt_options = Dict(
        :legend => false,
        :framestyle => :box,
        :grid => false,
        :size => (800,800),
        :axis => nothing
    ),
    line_options = Dict(
        :linecolor => :blue,
        :linewidth => linewidth,
        :linealpha => linealpha)
    )
)
```

optigraph `graph` のグラフレイアウトをプロットします。グラフレイアウトをカスタマイズするために提供できるキーワード引数は以下の通りです。

  * `node_labels = false`: 対応するオプティノードラベル属性を使用してノードにラベルを付けるかどうか。
  * `subgraph_colors = false`: サブグラフに従ってノードに色を付けるかどうか。
  * `node_colors = false`: ノードに色を付けるかどうか。 `subgraph_colors = false` の場合のみ有効。
  * `linewidth = 2.0`: `graph` の各エッジのライン幅属性。
  * `linealpha = 1.0`: `graph` の各エッジのラインアルファ属性。
  * `markersize = 30`: `graph` の各ノードのサイズを決定するマーカーサイズ。
  * `labelsize = 20`: 各ノードラベルのサイズ。 `node_labels = true` の場合のみ有効。
  * `markercolor = :grey`: 各ノードの色。
  * `layout_options = Dict(:tol => 0.01,:C => 2, :K => 4, :iterations => 2)`: レイアウトアルゴリズムのオプションを含む辞書。

      * `tol`: 現在の座標と計算された座標の間の許可される距離。
      * `C`,`K`: スケーリングパラメータ。
      * `iterations`: 力を適用するために使用される反復回数。
  * `plt_options = Dict(:legend => false,:framestyle => :box,:grid => false,:size => (800,800),:axis => nothing)`: 主なプロットオプションを含む辞書。

      * `legend`: 凡例を含めるか、または凡例の位置。
      * `framestyle`: プロットに使用されるフレームのスタイル。
      * `size`: 結果のプロットのサイズ。
      * `axis`: 軸を含めるかどうか。グラフレイアウトプロットには通常、軸は意味を持ちません。
      * `Plots.jl` パッケージの `Plots.scatter` と互換性のあるさまざまなプロットオプションを使用することも可能です。
  * `line_options = Dict(:linecolor => :blue,:linewidth => linewidth,:linealpha => linealpha)`: グラフ内のエッジを表示するために使用されるラインプロットオプション。

      * `linecolor`: 各ラインに使用する色。
      * `linewidth`: 各エッジに使用するライン幅。上記のオプションがデフォルト。
      * `linealpha`: 各エッジに使用するラインアルファ。上記のオプションがデフォルト。
