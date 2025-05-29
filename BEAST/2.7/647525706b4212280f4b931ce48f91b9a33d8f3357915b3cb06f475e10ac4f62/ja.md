```
raviartthomas(mesh)
```

入力 `mesh` に対して前処理を行い、RT基底を構築するために必要なセルエッジ、セルペア、およびインデックスを抽出します。

raviartthomas(mesh::Mesh, cellpairs::Array{Int,2}) を呼び出し、特定されたセルペアを使用して `mesh` 上にRT基底を構築します。

RT基底オブジェクトを返します。
