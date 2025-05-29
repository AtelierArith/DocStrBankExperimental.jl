```
BezierPath(commands::Vector)
```

ベジェパスをパスコマンドのベクターで構築します。利用可能なパスコマンドは次のとおりです。

  * `MoveTo`
  * `LineTo`
  * `CurveTo`
  * `EllipticalArc`
  * `ClosePath`

`BezierPath`は、Makieの特定の場所でポリゴンや線のコレクションの代わりに使用でき、例えば`poly`や`lines`への入力、または`scatter`の`marker`として使用できます。

`BezierPath`を使用する利点は、ユーザーが曲線を頂点のベクターに変換する必要がないことです。CairoMakieは、ベクターグラフィックスを描画する際にパスコマンドを直接使用できるため、視覚的に線分を使用して近似するよりも効率的で、スペースを節約できます。
