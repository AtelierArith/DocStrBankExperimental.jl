```
boundary_condition_pressure_in(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations1D)
```

時間とともに変化する流入圧力の境界条件を実装します。

### パラメータ

  * `u_inner`: 境界近くの領域内の状態ベクトル。
  * `orientation_or_normal`: 境界の法線方向。
  * `direction`: 境界の方向を示す整数。
  * `x`: 位置ベクトル。
  * `t`: 時間スカラー。
  * `surface_flux_function`: 境界でのフラックスを計算する関数。
  * `eq`: `BloodFlowEquations1D`のインスタンス。

### 戻り値

流入圧力によって指定された計算された境界フラックス：

$$
P_{in} = \begin{cases}
2 \times 10^4 \sin^2(\pi t / 0.125) & \text{if } t < 0.125 \\
0 & \text{otherwise}
\end{cases}
$$

対応する流入面積 `A_{in}` は逆圧力関係を使用して計算され、境界状態はそれに応じて構築されます。
