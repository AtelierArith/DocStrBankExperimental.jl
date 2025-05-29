```
struct DeltaComplex
```

表面の三角形分割を表すグラフデータ構造。

`DeltaComplex`は三角形分割の双対と考えることができます。

頂点は三角形の面（`TriFace`）です。すべての頂点には、それに接続する三つの辺（`DualEdge`）があります。
