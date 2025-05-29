```
AffineTransform
```

アフィン変換を表す型で、値をある単位から別の単位に変換するために使用できます。これは `uconvert(u::AbstractUnitLike, u0::AbstractUnitLike)` の出力型です。このオブジェクトは呼び出し可能です。

# フィールド

  * scale :: Float64
  * offset :: Float64

# コンストラクタ

  * AffineTransform(scale::Real, offset::Real)
  * AffineTransform(; scale, offset)
