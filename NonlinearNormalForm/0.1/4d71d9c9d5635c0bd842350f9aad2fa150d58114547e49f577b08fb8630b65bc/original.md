```
TaylorMap{S,T<:TPS,U<:Union{Quaternion{T},Nothing},V<:Union{Matrix,Nothing},W<:Union{Nothing,Bool}}
```

Abstract type for `TPSAMap` and `DAMap` used for normal form analysis. 

All `TaylorMap`s contain `x0` and `x` as the entrance coordinates and transfer map  as a truncated power series respectively. If spin is included, a field `Q` containing  a `Quaternion` as a truncated power series is included, else `Q` is `nothing`. If  stochasticity is included, a field `E` contains a matrix of the envelope for the FD kicks, else `E` is nothing.

If all planes are exhibiting pseudo-harmonic oscillations, then `idpt` is `nothing`.  If the last plane is coasting, then `idpt` specifies which variable in the last plane  is constant (energy-like): `idpt=false` if the variable with index `NV-1` is constant, or  `idpt=true` is the variable with index `NV` is constant.

### Fields

  * `x0`   – Entrance coordinates of the map, Taylor expansion point
  * `x`    – Orbital ray as a truncated power series, expansion around `x0` + scalar part equal to EXIT coordinates of map
  * `Q`    – `Quaternion` as a truncated power series if spin is included, else `nothing`
  * `E`    – Matrix of the envelope for FD kicks if included, else `nothing`
  * `idpt` – If the last plane is coasting, then `idpt=false` if the first variable in last plane is constant (energy-like) or `true` if the second. If no coasting, then `idpt=nothing`
