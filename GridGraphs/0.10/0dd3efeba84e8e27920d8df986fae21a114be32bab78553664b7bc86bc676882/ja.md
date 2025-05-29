```
GridDirection
```

2次元グリッドの正方形セル上での9つの可能な移動方向のための列挙型: `northwest`、`west`、`southwest`、`north`、`center`、`south`、`northeast`、`east`、`southeast`。

これらの方向のさまざまな部分集合が定数として定義されています。これらはチェスのゲームとの類似に基づいています：

  * `QUEEN_DIRECTIONS`
  * `ROOK_DIRECTIONS`
  * `QUEEN_DIRECTIONS_PLUS_CENTER`
  * `ROOK_DIRECTIONS_PLUS_CENTER`
  * `QUEEN_DIRECTIONS_ACYCLIC`
  * `ROOK_DIRECTIONS_ACYCLIC`

非循環方向セットは、`{south, east, southeast}`に含まれているため、非循環グラフを生じさせます。
