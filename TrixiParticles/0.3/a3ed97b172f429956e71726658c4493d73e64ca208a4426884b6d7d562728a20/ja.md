```
LinearContactModel(; normal_stiffness)
```

線形スプリング-ダッシュポット接触モデル ([Cundall1979](@cite))。

このモデルは、弾性成分のための線形スプリング法則と、散逸成分のための線形粘性減衰法則に基づいて、2つの物体間の法線接触力を計算します。総法線力 $F_n$ は次のように与えられます。

$$
F_n = k_n \delta + \gamma_d v_{\text{rel,n}},
$$

ここで、$k_n$ は法線剛性、$\delta$ は物体間の重なり、$v_{\text{rel,n}}$ は相対速度の法線成分、$\gamma_d$ は減衰係数です。

減衰係数 $\gamma_d$ は、臨界減衰係数 $\gamma_c$ とユーザーが提供する減衰比 $C_{\text{damp}}$ に基づいて計算されます。

$$
\gamma_d = C_{\text{damp}} \gamma_c,
$$

ここで、この線形システムの臨界減衰は次のように表されます。

$$
\gamma_c = 2 \sqrt{m^* k_n}
$$

および $m^*$ は衝突するペアの有効質量です。

総力は、接触する物体の中心を結ぶ法線方向に適用されます。

# フィールド

  * `normal_stiffness::Real`: 法線方向の定数スプリング剛性 $k_n$。
