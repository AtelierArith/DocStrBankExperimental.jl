```
 divexact(a::KInftyElem{T}, b::KInftyElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

与えられた局所化の要素 'c' を返します。これは $a = bc$ となる要素です。もしそのような要素が存在する場合です。`checked = false` の場合、対応する有理関数体の要素が返され、与えられた局所化の要素であるかどうかはチェックされません。
