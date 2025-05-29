```
evaluate(a::MPolyRingElem{T}, vars::Vector{Int}, vals::Vector{U}) where {T <: RingElement, U <: RingElement}
```

多項式式を評価し、配列 `vals` に供給された値を、配列 `vars` で与えられたインデックスの対応する変数に代入します。評価は、$a$ の係数環の要素と `vals` の要素の間で乗算が定義されている場合に成功します。
