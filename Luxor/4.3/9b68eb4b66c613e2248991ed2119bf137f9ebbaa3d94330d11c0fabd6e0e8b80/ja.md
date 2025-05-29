A Pathオブジェクトは、`.path`フィールドにCairoパスを記述する`PathElement`（`PathCurve`、`PathMove`、`PathLine`、`PathClose`）のベクターを含みます。`drawpath()`を使用して描画します。

```julia
Path([PathMove(Point(2.0, 90.5625)),
      PathCurve(Point(4.08203, 68.16015), Point(11.28, 45.28), Point(24.8828, 26.40234)),
      PathLine(Point(2.0, 90.5625)),
      PathClose()
     ])
```
