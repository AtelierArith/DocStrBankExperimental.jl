```
  (O::NumFieldOrder)(a::NumFieldElem, check::Bool = true) -> NumFieldOrderElem
```

Given an element $a$ of the ambient number field of $\mathcal O$, this function coerces the element into $\mathcal O$. It will be checked that $a$ is contained in $\mathcal O$ if and only if `check` is `true`.
