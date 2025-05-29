```
regulator(u::Vector{T}, C::qAdicConj, n::Int = 10; flat::Bool = true) where {T<: Union{AbsSimpleNumFieldElem, FacElem{AbsSimpleNumFieldElem, AbsSimpleNumField}}}
regulator(K::AbsSimpleNumField, C::qAdicConj, n::Int = 10; flat::Bool = true)
regulator(R::AbsNumFieldOrder, C::qAdicConj, n::Int = 10; flat::Bool = true)
```

$ m^t m $ の行列式を返します。ここで、$ m $ の列は、配列内の単位の `conjugates_log` であるか、$ K $（$ K $ の最大の順序）または $ R $ の基本単位です。`flat = false` の場合、$ p $ 上のすべての素イデアルは同じ次数を持つ必要があります。いずれの場合も、レオポルドの予想は、単位が依存している場合に限り、レギュレーターがゼロであると述べています。
