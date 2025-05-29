```julia
xpnorm(
    p::Float64,
    dv::AbstractDict{Tuple{Int64, Int64}, AbstractVector{Float64}},
    w::AbstractVector{Float64}
) -> Float64

```

返す値は $\Vert f \Vert^p_{X_p(\Omega)} = \int_{\Omega} \Vert ∇ f(x) \Vert_2^p \;\mathrm{d}x$ であり、FEM 表現においては次のようになります。

$$
\Vert f \Vert^p_{X_p(T_{h_\Omega})} =
    \sum\limits_{i=1}^m \omega_i 
    \left(\sum\limits_{j=1}^d \sum\limits_{r=1}^{d^\prime}
    [D^{(j,r)} v]_i^2 \right)^{\frac{p}{2}}.
$$

パラメータは、関数とメッシュとして与えることも、関数を FEM コエフィシエントベクトルとして与え、導関数テンソルとすることもできます。

# 必須引数

  * `p::Float64`: ノルムのパラメータ。
  * `dv::AbstractDict{Tuple{Int64,Int64},AbstractVector{Float64}}`: $T_{h_\Omega}$ の要素のガウス点で与えられた関数 v の離散導関数。
  * `w::AbstractVector{Float64}`: ガウス点に対応する重みのベクトル。
