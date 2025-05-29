```
spectral_to_imaginary_time_correlation_function(;
    # キーワード引数
    τ::AbstractVector{T},
    β::T,
    spectral_function::Function,
    kernel_function::Function,
    tol::T = 1e-10,
    bounds = (-Inf, +Inf),
    normalize::Bool = false
) where {T<:AbstractFloat}
```

虚時間相関関数を計算して返します

$$
C(\tau) = \int_{-\infty}^{\infty} d\omega \ K_\beta(\omega, \tau) \ A(\omega).
$$

スペクトル関数 $A(\omega)$ (`spectral_function`) とカーネル関数 $K_\beta(\omega,\tau)$ (`kernel_function`) が与えられたとき、$\tau$ (`τ`) 値のグリッド上で評価されます。この積分は指定された許容誤差 `tol` 内で評価されます。

## 引数

  * `τ::AbstractVector{T}`: 虚時間のベクトルで、`τ[end] = β` は逆温度に等しい。
  * `spectral_function::Function`: 単一の引数を取るスペクトル関数 $A(\omega)$。
  * `kernel_function::Function`: 上記のように3つの引数を取るカーネル関数 $K_\beta(\omega,\tau)$。
  * `tol::T = 1e-10`: $C(\tau)$ が評価される精度。
  * `bounds = (-Inf, +Inf)`: 積分領域の境界。
  * `normalize::Bool = false`: スペクトル関数を1に正規化する必要があるかどうか。
