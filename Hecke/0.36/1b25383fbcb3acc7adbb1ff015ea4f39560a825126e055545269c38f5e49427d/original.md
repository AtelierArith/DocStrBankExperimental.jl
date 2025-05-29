```
ideal(O::RelNumFieldOrder{T, S}, a::S; check::Bool = true) -> RelNumFieldOrderIdeal{T, S}
```

Creates the ideal $a \cdot \mathcal O$ of $\mathcal O$. If `check` is set, then it is checked whether $a$ defines an (integral) ideal.
