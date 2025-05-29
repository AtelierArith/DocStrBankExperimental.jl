```
Object{S, D, V, C, A, Da}(center, width, angle, value) <: AbstractObject
    where {S <: AbstractShape, V <: Number, C,A <: RealU}

2Dおよび3Dオブジェクトの一般的なコンテナで、画像ファントムを定義します。

  * `center::NTuple{D,C}` このオブジェクトの「中心」の座標
  * `width::NTuple{D,C}` 各軸に沿った「幅」（例：ガウスのFWHM、楕円の半径）
  * `angle::NTuple{D-1,A}` x軸に対するx'軸の角度、ラジアン（または単位付き）
  * `value::V` このオブジェクトの「強度」値

# 例

```

jldoctest julia> Object(Ellipse(), (0,0), (1,2), 0.0, 1//2) Object2d{Ellipse, Rational{Int64}, Int64, Float64, 1, Float64} (S, D, V, ...)  center::NTuple{2,Int64} (0, 0)  width::NTuple{2,Int64} (1, 2)  angle::Tuple{Float64} (0.0,)  value::Rational{Int64} 1//2 ```
