```
QuasiRectangularProfile{V,T,L}
```

このエンベロープは、幅 $Δz$ の主に一定の部分を持つパルスを生成し、空間プロファイルに対して考慮されるパラキシアル制限においてガウスプロファイルよりも良い結果を提供する可能性があります。エンベロープの形状は次のように与えられます。

$$
envelope(z, t) =
    \begin{cases}
    \exp\left[-\left(\frac{φ + Δt/2}{τ}\right)^2\right], & \text{for } φ ≤ \frac{Δt}{2}\\
    1\,, & \text{for } \text{otherwise}\\
    \exp\left[-\left(\frac{φ - Δt/2}{τ}\right)^2\right], & \ φ > \frac{Δt}{2}
    \end{cases}
$$

ここで

$$
\varphi = (t - t_0) - \frac{z - z_0}{c}\,,
$$

および

  * `c` は光の速度です
  * `τ` はパルスの持続時間（FWHM）で、デフォルト値は 18.02fs です
  * `t₀` は時間軸の起点で、デフォルトでは 0 です
  * `z₀` は強度ピークの初期位置で、デフォルト値は `-4*τ*c` です
  * `Δt` はプロファイルの平坦部分の持続時間で、デフォルト値は `10*τ` です
