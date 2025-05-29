```julia
getVariables(dfg; ...)
getVariables(dfg, regexFilter; tags, solvable, detail)

```

DFG内のDFGVariablesをリストします。オプションで、変数のサブセットを取得するためにラベルの正規表現を指定できます。Tagsは、ノードが持つ必要がある任意のタグのリストです（少なくとも1つの一致）。
