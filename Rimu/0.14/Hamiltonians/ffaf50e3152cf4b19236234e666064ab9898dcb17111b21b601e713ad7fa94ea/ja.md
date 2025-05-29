```
HubbardMom1DEP(address; u=1.0, t=1.0, v_ho=1.0, dispersion=hubbard_dispersion)
```

運動量空間における一次元ボース・ハバードチェーンを実装します。外部の調和ポテンシャルを持っています。

$$
Ĥ = \sum_{k} ϵ_k n_k + \frac{u}{M}\sum_{kpqr} a^†_{r} a^†_{q} a_p a_k δ_{r+q,p+k}
            + V̂_\mathrm{ho} ,
$$

ここで

$$
\begin{aligned}
V̂_\mathrm{ho} & = \frac{1}{M} \sum_{p,q}  \mathrm{DFT}[V_{ext}]_{p-q} \,
                    a^†_{p} a_q ,\\
V_\mathrm{ext}(x) &= v_\mathrm{ho} \,x^2 ,
\end{aligned}
$$

は運動量空間における外部の調和ポテンシャルであり、$\mathrm{DFT}[…]_k$は`fft()[k%M + 1]`によって行われる離散フーリエ変換であり、`M == num_modes(address)`です。

# 引数

  * `address`: 開始アドレスで、粒子数とサイト数を定義します。
  * `u`: 相互作用パラメータ。
  * `t`: ホッピング強度。
  * `dispersion`: $ϵ_k =$`dispersion(t, k)`を定義します。

      * [`hubbard_dispersion`](@ref): $ϵ_k = -2[\Re(t) \cos(k) + \Im(t) \sin(k)]$
      * [`continuum_dispersion`](@ref): $ϵ_k = \Re(t) k^2 - 2 \Im(t) k$
  * `v_ho`: 外部調和振動子ポテンシャルの強度 $v_\mathrm{ho}$。

さらに[`HubbardMom1D`](@ref)、[`HubbardReal1DEP`](@ref)、[`Transcorrelated1D`](@ref)、[`Hamiltonians`](@ref)も参照してください。
