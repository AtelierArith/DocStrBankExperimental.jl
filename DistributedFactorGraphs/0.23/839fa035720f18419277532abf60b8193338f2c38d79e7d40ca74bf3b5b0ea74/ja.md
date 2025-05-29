```julia
listVariables(dfg; ...)
listVariables(dfg, regexFilter; tags, solvable)

```

グラフ内のDFGVariablesのラベルのリストを取得します。オプションで、変数のサブセットを取得するためのラベルの正規表現を指定できます。タグは、ノードが持つ必要がある任意のタグのリストです（少なくとも1つの一致）。

ノート

  * `::Vector{Symbol}`を返します

例

```julia
listVariables(dfg, r"l", tags=[:APRILTAG;])
```

関連情報: [`ls`](@ref)
