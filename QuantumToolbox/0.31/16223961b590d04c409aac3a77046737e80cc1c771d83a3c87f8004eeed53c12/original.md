```
w_state(n::Union{Int,Val})
```

Returns the `n`-qubit [W-state](https://en.wikipedia.org/wiki/W_state):

$$
\frac{1}{\sqrt{n}} \left( |100...0\rangle + |010...0\rangle + \cdots + |00...01\rangle \right)
$$

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `w_state(Val(n))` instead of `w_state(n)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) for more details.

