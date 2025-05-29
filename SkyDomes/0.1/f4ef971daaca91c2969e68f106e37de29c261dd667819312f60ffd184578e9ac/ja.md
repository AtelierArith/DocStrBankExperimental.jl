```
sky(mesh; Idir = 0.77, nrays_dir = 100_000, theta_dir = 0.0, phi_dir = 0.0,
           Idif = 0.23, nrays_dif = 1_000_000, sky_model = StandardSky,
           dome_method = equal_solid_angles, ntheta = 9, nphi = 12,
           kwargs...)
```

与えられたメッシュに対して、拡散および直接太陽放射を表す方向性放射源のベクトルを作成します。

# 引数

  * `mesh`: VPLによって生成されたメッシュオブジェクト。
  * `Idir`: 水平面で測定された直接太陽放射（単一の値またはタプル）。
  * `nrays_dir`: 直接太陽放射のために生成されるレイの数。
  * `theta_dir`: 太陽位置の天頂角（ラジアン）。
  * `phi_dir`: 太陽位置の方位角（ラジアン）。
  * `Idif`: 水平面で測定された拡散太陽放射（単一の値またはタプル）。
  * `nrays_dif`: 拡散太陽放射のために生成されるレイの総数。
  * `sky_model`: 拡散放射照度の角度分布（`StandardSky`、`UniformSky`または`CIE`）。
  * `dome_method`: 拡散太陽放射のために半球をパッチに離散化する方法（`equal_solid_angles`または`equal_angle_intervals`）。
  * `ntheta`: `dome_method`の天頂角に沿った分割数。
  * `nphi`: `dome_method`の方位角に沿った分割数。
  * `kwargs...`: `dome_method = CIE`のときに使用される追加の引数。

# 戻り値

VPLでのレイトレーシング計算に使用できる方向性ソースのベクトル。 ```
