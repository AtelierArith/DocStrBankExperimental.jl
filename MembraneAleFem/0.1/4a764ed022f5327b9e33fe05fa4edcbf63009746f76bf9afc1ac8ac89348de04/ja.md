```
ノイマン
```

ノイマン境界条件の種類を列挙します: `instances(Neumann)`

  * `SHEAR     = 1` –> τ方向に面内力/長さを適用
  * `STRETCH   = 2` –> ν方向に面内力/長さを適用
  * `MOMENT    = 3` –> 境界モーメントを適用

関連する有限要素計算は[`calc_bdry_element_residual`](@ref)にあります。
