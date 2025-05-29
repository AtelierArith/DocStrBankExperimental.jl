```
 divexact(a::OrdLocElem{T}, b::OrdLocElem{T}, checked::Bool = true)  where {T <: AbsSimpleNumFieldElem}
```

与えられた局所化の要素 'c' を返します。すなわち、`c`*$b$ = $a$ となる要素が存在する場合です。'checked = false' の場合、対応する数体の要素が返され、与えられた局所化の要素であるかどうかはチェックされません。
