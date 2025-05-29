```
CosSquarePulse(mom::M,pulse_length::T) where {M<:QEDbase.AbstractFourMomentum,T<:Real}
```

コサイン二乗パルスのための `AbstractPulsedPlaneWaveField` の具体的な実装です。

!!! note "パルス形状"
    コサイン二乗パルスのパルスエンベロープは次のように定義されます。

    $$
    g(\phi) = \cos^2(\frac{\pi\phi}{2\Delta\phi})
    $$

    ただし、$\phi\in (-\Delta\phi,\Delta\phi)$ の場合であり、そうでない場合はゼロです。

