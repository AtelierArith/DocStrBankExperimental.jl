```
decodemoves(bytes::Vector{UInt8}; annotations = false, fen = START_FEN)
```

`encodemoves`によって作成されたバイト配列をゲームに戻します。

`annotations`が`false`の場合、返り値は`SimpleGame`ですが、`true`の場合、返り値は`Game`です。
