```
evaluate(a::S, vars::Vector{S}, vals::Vector{U}) where {S <: MPolyRingElem{T}, U <: RingElement} where T <: RingElement
```

多項式式を評価し、配列 `vals` に供給された値を、配列 `vars` によって与えられた対応する変数（多項式として供給される）に代入します。評価は、$a$ の係数環の要素と `vals` の要素の間で乗算が定義されている場合に成功します。
