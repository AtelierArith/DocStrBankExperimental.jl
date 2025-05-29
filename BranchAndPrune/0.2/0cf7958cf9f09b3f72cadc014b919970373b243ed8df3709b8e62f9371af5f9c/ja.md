```
SearchOrder
```

分岐と剪定検索中の処理順序を表す抽象型。

カスタム検索順序には、次のメソッドを実装する必要があります：

  * `pop!(so::SearchOrder)`: 次に処理するリーフを返します。検索が完了した場合は `nothing` を返します。
  * `push!(so::SearchOrder, leaf::BPNode)`: 処理するリーフのセットにリーフを追加します。

オブジェクトは、検索ツリーのルートノードを与えることで初期化されます。`SearchOrder(root::BPNode)`。
