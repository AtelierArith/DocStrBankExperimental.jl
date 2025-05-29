```
mutable struct Cell{S<:Coordinate}
```

セルは名前を持ち、ポリゴンと `CellArray` または `CellReference` オブジェクトへの参照を含みます。また、自身の作成時刻を記録します。現在の実装では、GDSIIファイルのセルの概念を反映しています。

要素を追加するには、`render!` を使用します。参照を追加するには、`addref!` または `addarr!` を使用します。テキストを追加するには、`text!` を使用します。
