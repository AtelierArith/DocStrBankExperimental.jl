```
SimpleGraph{T}(nv, ne, edgestream::Channel)
```

`edgestream` から `nv` 頂点と `ne` 辺を持つ `SimpleGraph{T}` を構築します。チャネル `edgestream` が早期に閉じられた場合、`ne` 辺未満になる可能性があります。重複する辺は一度だけカウントされます。要素の型は `nv` の型です。
