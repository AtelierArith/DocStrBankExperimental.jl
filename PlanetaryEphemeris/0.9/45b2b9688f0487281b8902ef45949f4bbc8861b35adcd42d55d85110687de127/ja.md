```
c2t_jpl_de430(t)
```

JPL DE 430/431 地球姿勢モデルに従った天体から地球座標への変換行列を返します。

$$
\texttt{c2t_jpl_de430}(t) = A\times C\times N,
$$

ここで、$t$ は J2000.0 からのユリウス日での TDB 時間、$A = R_z(-z_A(t))R_y(\theta_A(t))R_z(-\zeta_A(t))$ は歳差行列、$C = R_y(\phi_y(t))R_x(\phi_x(t))$ は線形補正行列、$N$ は摂動行列です。

https://doi.org/10.1002/0471728470 のページ (5-59) の式 (5-147) およびページ (5-60) の式 (5-152) を参照してください。また、https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract のページ 11 の式 (25) およびページ 50 の表 10 も参照してください。

[`Rx`](@ref)、[`Ry`](@ref)、[`Rz`](@ref) および [`nutation_iau80`](@ref) もご覧ください。
