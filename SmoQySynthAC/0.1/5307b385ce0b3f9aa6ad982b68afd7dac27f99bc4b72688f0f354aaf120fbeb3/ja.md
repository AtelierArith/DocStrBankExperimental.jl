```
spectral_to_matsubara_correlation_function(;
    # キーワード引数
    n::AbstractVector{Int},
    β::T,
    spectral_function::Function,
    kernel_function::Function,
    tol::T = 1e-10,
    bounds = (-Inf, 0.0, +Inf),
    normalize::Bool = false
) where {T<:AbstractFloat}
```

マツバラ相関関数を計算して返します

$$
C({\rm i} \omega_n) = \int_{-\infty}^{\infty} d\omega \ K_\beta(\omega, \omega_n) \ A(\omega).
$$

スペクトル関数 $A(\omega)$ (`spectral_function`) とカーネル関数 $K_\beta(\omega,\omega_n)$ (`kernel_function`) が与えられたとき、$n \in \mathbb{Z}$ の値のベクトルに対して計算されます。この積分は指定された許容誤差 `tol` 内で評価されます。

カーネル関数は `kernel_function(ω, n, β)` として呼び出されるべきであり、ここで `n` はマツバラ周波数を指定します。これは内部的に $\omega_n = (2n+1)\pi/\beta$ または $\omega_n = 2n\pi/\beta$ として評価され、カーネル関数がそれぞれフェルミオンまたはボソンであるかに依存します。

## 引数

  * `n::AbstractVector{Int}`: $C({\rm i}\omega_n)$ が評価されるマツバラ周波数を指定する整数のベクトル。
  * `spectral_function::Function`: 単一の引数を取るスペクトル関数 $A(\omega)$。
  * `kernel_function::Function`: 三つの引数を取るカーネル関数 $K_\beta(\omega,\omega_n)$。
  * `tol::T = 1e-10`: $C({\rm i}\omega_n)$ が評価される精度。
  * `bounds = (-Inf, +Inf)`: 積分領域の境界。
  * `normalize::Bool = false`: スペクトル関数を1に正規化する必要があるかどうか。
