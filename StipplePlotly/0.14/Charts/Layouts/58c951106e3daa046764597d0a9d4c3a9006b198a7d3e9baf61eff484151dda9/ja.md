```
  GeoProjection()
```

---

# 例

---

```
julia>
```

---

# プロパティ

---

  * `distance::Float64` - 衛星投影タイプのみ。球の中心から視点までの距離を球の半径の割合として設定します。タイプ: `1.001`以上の数値 | デフォルト: `2`
  * `parallels::Vector{Float64}` - 円錐投影タイプのみ。円錐が球と交差する平行線（接線、割線）を設定します。
  * `rotation::Protation` - 詳細についてはProtation構造体を確認してください
  * `scale::Float64` - 地図ビューをズームインまたはズームアウトします。スケールが「1」の場合、地図の経度と緯度の範囲に収まる最大のズームレベルに対応します。`0`以上の数値 | デフォルト: `1`
  * `tilt::Float64` - 衛星投影タイプのみ。透視投影の傾斜角を設定します。タイプ: `数値` | デフォルト: `0`
  * `type::String` - 投影タイプを設定します。タイプ: 列挙型、次のいずれか（ `"albers"` | `"albers usa"` | `"azimuthal equal area"` | `"azimuthal equidistant"` | `"conic equal area"` | `"conic conformal"` | `"conic equidistant"` | `"equidistant conic"` | `"gnomonic"` | `"mercator"` | `"natural earth"` | `"orthographic"` | `"stereographic"` | `"transverse mercator"` ）
