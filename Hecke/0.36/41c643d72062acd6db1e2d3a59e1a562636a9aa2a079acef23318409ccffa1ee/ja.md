```
 divides(a::OrdLocElem{T}, b::OrdLocElem{T}, checked::Bool = true) where {T <: AbsSimpleNumFieldElem}
```

$ b $ が $ a $ を割り切る場合、タプル (`true`,`c`) を返します。ここで `c`*$b$ = $a$ です。'checked = false' の場合、対応する数体の要素が返され、与えられた局所化の要素であるかどうかはチェックされません。
