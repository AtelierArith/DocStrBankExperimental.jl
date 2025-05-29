```
groupreduce(by, f, op, iter...; [init])
```

`iter`の要素を`by`を通して渡すことによってラベル付けされたグループに対して`mapreduce`のような操作を適用します。主に`map(g -> reduce(op, g), group(by, f, iter))`と同等ですが、より効率的に設計されています。複数のコレクション（同じ長さのもの）が提供される場合、変換`by`と`f`は要素ごとに行われます。
