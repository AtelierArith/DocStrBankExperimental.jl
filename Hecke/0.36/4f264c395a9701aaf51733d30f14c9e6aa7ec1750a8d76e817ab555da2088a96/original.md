```
ideal(O::RelNumFieldOrder{T, S}, x::RelSimpleNumFieldElem{T}, y::RelSimpleNumFieldElem{T}, a::S, b::S; check::Bool = true) -> RelNumFieldOrderIdeal{T, S}
```

Creates the ideal $x\cdot a + y\cdot b$ of $\mathcal O$. If `check` is set, then it is checked whether these elements define an ideal.
