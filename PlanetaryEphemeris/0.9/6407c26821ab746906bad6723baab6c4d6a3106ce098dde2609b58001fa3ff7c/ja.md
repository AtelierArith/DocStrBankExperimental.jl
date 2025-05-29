```
pole_rotation(α::T, δ::T, W::T=zero(α)) where {T <: Number}
```

慣性座標系から、赤経 $\alpha$、赤緯 $\delta$、および本初子午線 $W$ を持つ座標系への回転行列を返します。

$$
A = R_z(W + \Delta W)R_x\left(\frac{\pi}{2} - \delta - \Delta\delta\right)R_z\left(\alpha + \Delta\alpha + \frac{\pi}{2}\right).
$$

https://doi.org/10.1002/0471728470 の6-5ページの式(6-3)を参照してください。

$$
\textbf{注意:}
$$

回転行列 $(R_x, R_y, R_z)$ の規約は、https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract の9ページの式(11)、(12)、(13)と同じです。

また、[`Rx`](@ref) と [`Rz`](@ref) も参照してください。
