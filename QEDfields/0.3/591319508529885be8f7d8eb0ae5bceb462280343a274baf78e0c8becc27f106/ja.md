```
GaussianPulse(mom::M,pulse_length::T) where {M<:QEDbase.AbstractFourMomentum,T<:Real}
```

ガウスパルスのための `AbstractPulsedPlaneWaveField` の具体的な実装です。

参照モーメントベクトル k*mu = (omega/speed*of*light, k*x, k*y, k*z) の空間的成分によって与えられた方向に沿って伝播し、omega = 2*pi*speed*of*light/wavelength です。

時間的座標 omega/speed*of*light の k_mu は、場の振動周波数を定義します。

真空の分散関係を満たすためには、k_mu*k^mu=0 が必要です。

!!! note "パルス形状"
    ガウスパルスの縦のエンベロープは次のように定義されます。

    $$
    g(\phi) = \exp(-\frac{\phi^2}{2\Delta\phi^2})
    $$

    ここで $\phi\in (-\infty, \infty)$ であり、$\Delta\phi$ は `pulse_length` を示します。

    横方向にはエンベロープはありません。

