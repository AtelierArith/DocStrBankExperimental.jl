```
generic_spectrum(field::AbstractPulsedPlaneWaveField, pol::AbstractDefinitePolarization, pnum)
```

与えられた場の一般的なスペクトルを、与えられた偏光方向 `pol` と与えられた光子数パラメータ `pnum` に対して返します。

!!! note "慣例"
    一般的なスペクトルは、与えられた偏光方向に対するそれぞれの振幅関数のフーリエ変換として定義されます：

    $$
    \begin{align*}
        x-\mathrm{pol} &\to \int_{-\infty}^{\infty} g(\phi) \cos(\phi) \exp(il\phi)\\
        y-\mathrm{pol} &\to \int_{-\infty}^{\infty} g(\phi) \sin(\phi) \exp(il\phi)
    \end{align*}
    $$

    ここで $g(\phi)$ は [`envelope`](@ref) であり、$l$ は光子数パラメータです。

