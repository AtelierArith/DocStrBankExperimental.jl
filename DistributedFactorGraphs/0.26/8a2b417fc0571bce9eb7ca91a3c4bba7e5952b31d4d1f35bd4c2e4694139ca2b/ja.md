```julia
isVariable(dfg, sym)

```

`sym::Symbol` がグラフ DFG の変数頂点を表すかどうかを返します。グラフに存在し、かつ変数であるかどうかをチェックします。（型のために簡単に確認したい場合は、単に `node isa VariableCompute` を実行してください。）
