```
CartesianIC{T<:AbstractFloat} <: InitialConditions{T}
```

初期条件は、各天体の直交座標と質量によって指定されます。

# フィールド

  * `x::Matrix{T}` : 各天体の位置 [次元, 天体]。
  * `v::Matrix{T}` : 各天体の速度 [次元, 天体]。
  * `m::Vector{T}` : 各天体の質量。
  * `nbody::Int64` : 系の天体の数。
  * `t0::T` : 初期時間。
