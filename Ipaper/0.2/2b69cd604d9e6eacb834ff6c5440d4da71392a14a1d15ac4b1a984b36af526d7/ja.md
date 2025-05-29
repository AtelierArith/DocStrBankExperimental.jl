```
approx(x, y, xout; rule=2)
```

与えられた点での関数の値を線形補間を使用して近似します。

> `DateTime` もサポートされています。しかし `Date` はサポートされていません！


# 引数

  * `x::AbstractVector{Tx}`: データポイントの x 座標。
  * `y::AbstractVector{Ty}`: データポイントの y 座標。
  * `xout::AbstractVector`: 近似する点の x 座標。
  * `rule::Int=2`: 使用する補間ルール。デフォルトは 2。

      * 1: NaN
      * 2: 最近接定数外挿
      * 3: 線形外挿
