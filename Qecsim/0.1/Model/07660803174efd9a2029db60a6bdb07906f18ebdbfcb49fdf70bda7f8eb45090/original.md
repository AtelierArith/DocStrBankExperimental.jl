```
logical_xs(code) -> BitMatrix
```

Return the logical X operators in binary symplectic form.

Each row is an operator. The order should match that of [`logical_zs`](@ref).

!!! note "Abstract method"
    This method should be implemented for concrete subtypes or duck-typed implementations of [`StabilizerCode`](@ref).

