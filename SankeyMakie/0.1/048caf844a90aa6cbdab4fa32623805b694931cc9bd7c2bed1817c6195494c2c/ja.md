```
sankey(connections; kwargs...)
```

接続の `(source, target, weight)` エントリからサンキー図をプロットします。

`sankey` に特有の属性は次のとおりです：

  * `compact = true`: 各層のノード間の垂直スペースを減らします。
  * `fontsize = theme(scene, :fontsize)`: ノードラベルのフォントサイズを設定します。
  * `nodelabels = nothing`: 対応するインデックスを持つラベルをノードの下に配置します。
  * `nodecolor = :gray30`: 各ノードの色を設定するか、1つの色が提供されている場合はすべてのノードに適用します。
  * `linkcolor = (:gray30, 0.2)`: 各リンクの色を設定するか、1つの色が提供されている場合はすべてのリンクに適用します。
  * `forceorder = Pair{Int,Int}[]`: 同じ層内のノードの順序を変更します。`[6 => 1]`（ノード6が1の前）や `:reverse`（すべての層内で逆順）にできます。

## 例

```julia
using CairoMakie, SankeyMakie
connections = [(1, 2, 10), (1, 3, 15), (3, 4, 5)]
sankey(connections; nodelabels = ["A", "B", "C", "D"])
```
