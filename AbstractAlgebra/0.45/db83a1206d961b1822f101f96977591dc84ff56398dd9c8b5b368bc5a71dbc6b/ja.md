```
inflate(f::MPolyRingElem, vars::Vector{Int}, shift::Vector{Int}, defl::Vector{Int})
```

与えられたシフト（再びシフトの配列として供給される）によって増加し、与えられたデフレーション指数（供給されたインフレーションファクターの配列として）によって膨張（乗算）された変数のいくつかの指数を持つが、$f$と同じ係数を持つ多項式を返します。
