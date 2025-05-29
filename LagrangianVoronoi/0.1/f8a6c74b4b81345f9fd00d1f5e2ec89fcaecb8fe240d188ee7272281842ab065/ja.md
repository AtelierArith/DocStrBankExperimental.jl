```
VoronoiPolygon
```

Voronoiポリゴンの抽象スーパタイプです。セルリストのセルとの混乱を避けるために、Voronoiポリゴンと呼び、Voronoiセルとは呼びません。Voronoiポリゴンのサブタイプに対して定義する必要がある関数はありませんが、以下のフィールドを持つことが求められます。

  * `x::RealVector`
  * `edges::FastVector{Edge}`

ここで、`x`は生成シードであり、`edges`は特に順序のないすべてのエッジのリストです。`edges`は`edges = emptypolygon()`として初期化でき、`remesh!`関数によって生成されます。サブタイプは、関与する物理に応じて追加のフィールドを含む場合があります。例については`src/celldefs.jl`を参照してください。
