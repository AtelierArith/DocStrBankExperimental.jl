```
edges = CodeEdges(src::CodeInfo)
```

`src`を分析し、依存関係のチェーンを特定します。

  * `edges.preds[i]`は、ステートメント`i`が依存している前のステートメントをリストします。
  * `edges.succs[i]`は、ステートメント`i`に依存している後のステートメントをリストします。
  * `edges.byname[v]`は、オブジェクト`v::GlobalRef`の前のステートメント、後のステートメント、および代入ステートメントに関する情報を返します。
