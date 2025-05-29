```
divexact_right(a::AlgAssAbsOrdElem, b::AlgAssAbsOrdElem; check::Bool = true)
divexact_right(a::AlgAssRelOrdElem, b::AlgAssRelOrdElem; check::Bool = true)
  -> AlgAssRelOrdElem
```

要素$c \in O$を返します。ここで、$a = c \cdot b$であり、$O$は$a$を含む順序です。`check`が`false`の場合、$c$が$O$の要素であるかどうかはチェックされません。
