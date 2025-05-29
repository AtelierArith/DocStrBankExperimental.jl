```julia
asdigraph(g::BipartiteGraph, sys::AbstractSystem; variables = unknowns(sys),
          equationsfirst = true)
```

[`BipartiteGraph`](@ref)を`LightGraph.SimpleDiGraph`に変換します。

ノート:

  * 結果の`SimpleDiGraph`は、2つの頂点集合（方程式と、[`asgraph`](@ref)から来る場合の未知数）を統合し、1つの順序付き整数頂点集合を生成します（`SimpleDiGraph`は2つの異なる頂点コレクションをサポートしていないため、マージする必要があります）。
  * `variables`は、`g`が関連付けられている変数を示します（通常はシステムの`unknowns`）。
  * `equationsfirst`（デフォルトは`true`）は、[`BipartiteGraph`](@ref)が方程式からそれらが依存する変数へのマッピングを提供するか（`true`）、[`asgraph`](@ref)によって計算された方程式を修正する変数へのマッピングを提供するか（`variable_dependencies`](@ref)によって計算された）を示します。

例: [`asgraph`](@ref)の例を続けると

```julia
dg = asdigraph(digr, jumpsys)
```
