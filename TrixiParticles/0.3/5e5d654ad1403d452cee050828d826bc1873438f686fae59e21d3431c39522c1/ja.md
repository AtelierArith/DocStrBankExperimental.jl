```
HertzContactModel(; elastic_modulus, poissons_ratio)
```

ハーツ接触モデルは、ハーツ接触理論に基づく非線形接触モデルです ([DiRenzo2004](@cite))。

このモデルは、2つの球状粒子（または等価な球で表される粒子と境界）間の法線接触力を、材料特性と重なり $\delta$ に基づいて計算します。力の弾性部分は次のように表されます：

$$
F_{\text{elastic}} = \frac{4}{3} E^* \sqrt{R^*} \delta^{3/2},
$$

ここで、$E^*$ は有効ヤング率、$R^*$ は有効半径です。

有効ヤング率 $E^*$ は、接触する2つの物体のヤング率 $E_a, E_b$ とポアソン比 $\nu_a, \nu_b$ から次のように計算されます：

$$
E^* = \left( \frac{1 - \nu_a^2}{E_a} + \frac{1 - \nu_b^2}{E_b} \right)^{-1}.
$$

有効半径 $R^*$ は、2つの粒子の半径 $R_a$ と $R_b$ から次のように計算されます：

$$
R^* = \left( \frac{1}{R_a} + \frac{1}{R_b} \right)^{-1} = \frac{R_a R_b}{R_a + R_b}.
$$

粒子-壁相互作用の場合、$R_b \to \infty$ となるため、$R^* = R_a$ です。

実装には、[DiRenzo2004](@cite) で説明されているアプローチに基づく減衰力も含まれており、相対速度の法線成分 $v_{\text{rel,n}}$ に比例します：

$$
F_{\text{damping}} = C_{\text{damp}} \gamma_c v_{\text{rel,n}},
$$

ここで、$C_{\text{damp}}$ はユーザーが提供する減衰係数（減衰比）、$\gamma_c$ は非線形臨界減衰係数です：

$$
\gamma_c = 2 \sqrt{m^* K_{\text{nonlin}}}
$$

ここで、$m^*$ は有効質量、$K_{\text{nonlin}}$ は現在の状態に関連する非線形剛性項です：

$$
K_{\text{nonlin}} = \frac{F_{\text{elastic}}}{\delta} = \frac{4}{3} E^* \sqrt{R^* \delta}.
$$

総法線力は $F_n = F_{\text{elastic}} + F_{\text{damping}}$ です。

# フィールド

  * `elastic_modulus::Float64`: 材料のヤング率 $E$。
  * `poissons_ratio::Float64`: 材料のポアソン比 $\nu$。
