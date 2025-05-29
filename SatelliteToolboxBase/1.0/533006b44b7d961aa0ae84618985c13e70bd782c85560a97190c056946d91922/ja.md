```
KeplerianElements{Tepoch<:Number, T<:Number} <: Orbit{Tepoch, T}
```

この構造体は、ケプラー要素を用いて軌道を定義します。

# フィールド

  * `t::Tepoch`: エポック。
  * `a::T`: 半長軸 [m]。
  * `e::T`: 離心率 [ ]。
  * `i::T`: 傾斜角 [rad]。
  * `Ω::T`: 昇交点の赤経 [rad]。
  * `ω::T`: 近点引数 [rad]。
  * `f::T`: 真異常 [rad]。
