```
ghz_state(n::Union{Int,Val}; d::Int=2)
```

Returns the generalized `n`-qudit [Greenberger–Horne–Zeilinger (GHZ) state](https://en.wikipedia.org/wiki/Greenberger%E2%80%93Horne%E2%80%93Zeilinger_state):

$$
\frac{1}{\sqrt{d}} \sum_{i=0}^{d-1} | i \rangle \otimes \cdots \otimes | i \rangle
$$

Here, `d` specifies the dimension of each qudit. Default to `d=2` (qubit).

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `ghz_state(Val(n))` instead of `ghz_state(n)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) for more details.

