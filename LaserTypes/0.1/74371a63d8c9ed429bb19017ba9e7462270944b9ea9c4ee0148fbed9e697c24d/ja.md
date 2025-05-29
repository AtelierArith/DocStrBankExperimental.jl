```
Cos²Profile{V,T,L}
```

このエンベロープはレーザーパルスの有限の持続時間を提供し、実際のレーザーパルスのより現実的な記述を提供することができます。

$$
envelope(z, t) =
    \begin{cases}
    \cos\left[\left(\frac{φ}{τ}\right)\right]^2, & \text{for } |t - t₀| < τ / 2\\
    0 \,, & \text{otherwise}
    \end{cases}
$$

ここで

$$
\varphi = (t - t_0) - \frac{z - z_0}{c}\,,
$$

および

  * `c` は光の速度です
  * `τ` はパルスの持続時間で、デフォルト値は18.02fsです
  * `t₀` は時間軸の起点で、デフォルトでは0です
  * `z₀` は強度ピークの初期位置で、デフォルトでは0です
