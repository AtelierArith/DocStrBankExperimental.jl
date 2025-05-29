```
remap(source_board::Board, target_board::Board)
```

`source_board`から生成されたゲームグラフの頂点を、`target_board`から生成されたゲームグラフに再マッピングします。`source_board`と`target_board`は同型でなければなりません。

```
remap(board::Board)
```

上記のように、`target_board`は`source_board`と同型で、最小のIDを持つ`Board`です。
