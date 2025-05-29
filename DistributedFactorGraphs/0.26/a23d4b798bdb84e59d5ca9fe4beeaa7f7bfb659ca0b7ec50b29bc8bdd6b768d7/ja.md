```julia
getVariables(dfg; ...)
getVariables(dfg, regexFilter; tags, solvable)

```

DFG内のDFGVariablesをリストします。オプションで、変数のサブセットを取得するためのラベル正規表現を指定できます。タグは、ノードが持つ必要がある任意のタグのリストです（少なくとも1つの一致）。
