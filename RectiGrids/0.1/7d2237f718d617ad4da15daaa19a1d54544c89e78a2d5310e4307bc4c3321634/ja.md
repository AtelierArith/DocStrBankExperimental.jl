```
grid([T], xs, ys, ...) -> RectiGrid
grid([T], x=xs, y=ys, ...) -> RectiGrid
```

`RectiGrid`オブジェクトを作成して、直交グリッドを表します。`AbstractArray`および`KeyedArray`インターフェースを実装しています。

位置引数`xs, ys, ...`を渡して名前のない次元のグリッドを作成するか、キーワード引数`x=xs, y=ys, ...`を渡して名前のある次元のグリッドを作成します。

型`T`は`Tuple`、または`T(::Tuple)`コンストラクタを持つ型（例：`SVector`）、または次元が名前付きの場合は`NamedTuple`であることができます。
