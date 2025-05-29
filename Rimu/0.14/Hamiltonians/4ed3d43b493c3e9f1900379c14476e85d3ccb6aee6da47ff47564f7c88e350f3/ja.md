```
ExtendedHubbardMom1D(
    address; 
    u=1.0, t=1.0, v=1.0, dispersion=hubbard_dispersion, boundary_condition = 0.0
)
```

1次元の拡張ハバードチェーン、別名$t - V$モデルを運動量空間で実装します。

$$
\hat{H} =  \sum_{k} ϵ_k n_k + \frac{1}{2M} \sum_{kpqr} (u + 2v \cos(q-p)) a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
$$

# 引数

  * `address`: 開始アドレス、粒子とサイトの数を定義します。
  * `u`: 相互作用パラメータ。
  * `t`: ホッピング強度。
  * `boundary_condition`: `θ <: Number`: 境界を越えるホッピングは、右へのホップに対して$\exp(iθ)$、左へのホップに対して$\exp(−iθ)$の因子がかかります。
  * `dispersion`: $ϵ_k =$`dispersion(t, k + θ)`を定義します。

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2 (\Re(t) \cos(k + θ) + \Im(t) \sin(k + θ))$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) (k + θ)^2 - 2 \Im(t) (k + θ)$

# 参照

  * [`HubbardMom1D`](@ref)
  * [`HubbardReal1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
