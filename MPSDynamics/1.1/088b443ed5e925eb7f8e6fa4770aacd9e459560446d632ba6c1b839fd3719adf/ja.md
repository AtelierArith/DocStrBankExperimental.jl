```
twobathspinmpo(ω0, Δ, Nl, Nr, dl, dr, chainparamsl=[fill(1.0,N),fill(1.0,N-1), 1.0], chainparamsr=chainparamsl; tree=false)
```

スピン-1/2が2つの調和振動子の鎖に結合されているMPOを生成します。これは次のハミルトニアンによって定義されます。

$$
H = \frac{ω_0}{2}σ_z + Δσ_x + c_0^rσ_x(b_0^\dagger+b_0) + \sum_{i=0}^{N_r-1} t_i^r (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N_r} ϵ_i^rb_i^\dagger b_i + c_0^lσ_x(d_0^\dagger+d_0) + \sum_{i=0}^{N_l-1} t_i^l (d_{i+1}^\dagger d_i +h.c.) + \sum_{i=0}^{N_l} ϵ_i^l d_i^\dagger d_i
$$

。

スピンはMPSのサイト$N_l + 1$にあり、左の鎖モードと右の鎖モードに囲まれています。

このハミルトニアンは、スピン-ボソンハミルトニアンによって定義されるものとユニタリに同等です（`N`サイトへの切り捨ての前に）。

$$
H =  \frac{ω_0}{2}σ_z + Δσ_x + σ_x\int_0^∞ dω\sqrt{J(ω)}(b_ω^\dagger+b_ω) + \int_0^∞ dω ωb_ω^\dagger b_ωi + σ_x\int_0^∞ dω\sqrt{J^l(ω)}(d_ω^\dagger+d_ω) + \int_0^∞ dω ωd_ω^\dagger d_ω
$$

。

鎖パラメータは、`chainparams`=$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$として供給され、任意の温度で任意のスペクトル密度$J(ω)$を表すように選択できます。2つの鎖は異なるスペクトル密度を持つことができます。
