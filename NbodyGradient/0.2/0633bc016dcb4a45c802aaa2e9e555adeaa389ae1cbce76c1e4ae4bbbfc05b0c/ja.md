```
ElementsIC{T<:AbstractFloat} <: InitialConditions{T}
```

初期条件は、階層ベクトルと軌道要素によって指定されます。

# フィールド

  * `elements::Matrix{T}` : 質量と軌道要素。
  * `ϵ::Matrix{T}` : ジャコビ座標の行列
  * `amat::Matrix{T}` : [Hamers and Portegies Zwart 2016](https://doi.org/10.1093/mnras/stw784)からの'A'行列。
  * `nbody::Int64` : 天体の数。
  * `m::Vector{T}` : 天体の質量。
  * `t0::T` : 初期時間 [日]。
