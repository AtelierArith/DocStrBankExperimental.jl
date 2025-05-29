```
evaluate(a::MPolyRingElem{T}, vals::Vector{U}) where {T <: RingElement, U <: RingElement}
```

多項式式を評価し、各変数の値の配列を代入します。評価は、$a$の係数環の要素と供給されたベクトルの要素の間で乗算が定義されている場合に成功します。
