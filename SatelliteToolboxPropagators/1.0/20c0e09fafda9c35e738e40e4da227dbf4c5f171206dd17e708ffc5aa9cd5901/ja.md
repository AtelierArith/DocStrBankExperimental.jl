```
struct J2PropagatorConstants{T<:Number}
```

J2軌道伝播器の定数。

# フィールド

  * `R0::T`: 地球の赤道半径 [m]。
  * `μm::T`: √(GM / R0^3) [er/s]^(3/2)。
  * `J2::T`: 地球の第二重力ゾナルハーモニック。
