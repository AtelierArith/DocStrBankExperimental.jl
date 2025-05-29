```
HubbardMom1D(address; u=1.0, t=1.0, dispersion=hubbard_dispersion)
```

1次元ボースハバードチェーンを運動量空間で実装します。

$$
\hat{H} =  \sum_{k} ϵ_k n_k + \frac{u}{M}\sum_{kpqr} a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
$$

# 引数

  * `address`: 開始アドレス、粒子数とサイト数を定義します。
  * `u`: 相互作用パラメータ。
  * `t`: ホッピング強度。
  * `dispersion`: $ϵ_k =$`dispersion(t, k)`を定義します。

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2(\Re(t) \cos(k) + \Im(t) \sin(k))$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) k^2 - 2 \Im(t) k$

# 参照

  * [`HubbardReal1D`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)
