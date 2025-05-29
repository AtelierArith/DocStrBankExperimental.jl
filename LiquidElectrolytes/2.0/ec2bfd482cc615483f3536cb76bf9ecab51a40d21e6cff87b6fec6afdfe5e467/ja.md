```
DGML_gamma!(γ, c, p, electrolyte)
```

ドライヤー、グールケ、ミュラー、ランストルファーによる活動係数。

$$
γ_i = \exp\left(\frac{\tilde v_i p}{RT}\right) \left(\frac{\bar c}{c_0}\right)^{m_i} \frac{1}{v_0\bar c}
$$

入力:

  * c: 濃度のベクトル
  * p: 圧力
  * electrolyte: [`ElectrolyteData`](@ref) のインスタンス

出力: 

  * γ (変更された) 活動係数

```
