```
LogarithmicNeutralWind(; monin_obukhov_stability_length = 0.4
                         charnock_coefficient = 0.014
                         air_kinematic_viscosity = 1.488e-5
                         gravity_wave_coefficient = 0.11
                         gravity = g_Earth,

                         precompute_drag_coefficients = false,
                         precompute_wind_speeds = [0:25/100000:25;],
                         arch = CPU())
```

表面摩擦係数のための `LogarithmicNeutralWind` パラメータ化を返します。

$$
C_d
$$

は次のようにパラメータ化されます。

$$
C_d = \left(\frac{\kappa}{\log{\frac{10}{z_0}}}\right)^2,
$$

ここで $\kappa$ はモニン‐オブコフ安定性長さ、$z_0$ は速度粗さ長さです。これは、相対速度を表面でゼロに対数的に持っていく粗さ長さスケールです。すなわち、

$$
U=\frac{u\star}{\kappa}\log\frac{z}{z_0},
$$

ここで $u\star$ は摩擦速度です。さらに、$z_0$ は次のように与えられます。

$$
z_0=b\frac{\nu}{u\star} + \frac{a_c}{g}u\star^2,
$$

ここで $\nu$ は空気の運動粘度、$g$ は重力加速度です。

このモデルは、これらの方程式を反復的に解いて $z_0$ を求めます。代わりに、フラグ `precomputed_roughness_length` が設定されている場合、`precompute_wind_speeds` で事前に計算され、その間で $z_0$ が実行時に補間されます。事前計算された速度は `arch` に適した型に変換されます（すなわち `CPU()` または `GPU()`）。

このパラメータ化は [smith1988](@citet) で説明されています。
