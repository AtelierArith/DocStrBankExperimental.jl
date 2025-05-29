```julia
isVariable(dfg, sym)

```

`sym::Symbol`がグラフDFGの変数頂点を表すかどうかを返します。グラフに存在し、かつ変数であるかどうかをチェックします。（タイプのために簡単に確認したい場合は、単に`node isa DFGVariable`を実行してください。）
