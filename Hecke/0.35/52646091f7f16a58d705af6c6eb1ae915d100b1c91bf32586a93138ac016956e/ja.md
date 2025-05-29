```
 divides(a::KInftyElem{T}, b::KInftyElem{T}, checked::Bool = true) where T <: FieldElement
```

タプル `(flag, c)` を返します。ここで `flag = true` であれば $b$ が $a$ を割り、$a = bc$ となります。そうでなければ `flag = false` で、$c = 0$ となります。`checked = false` の場合、対応する有理関数体の要素が返され、与えられた局所化の要素であるかどうかはチェックされません。
