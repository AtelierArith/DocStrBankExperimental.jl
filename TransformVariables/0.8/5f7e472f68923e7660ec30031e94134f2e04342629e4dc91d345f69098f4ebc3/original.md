```
as(Real, left, right)
```

Return a transformation that transforms a single real number to the given (open) interval.

`left < right` is required, but may be `-∞` or `∞`, respectively, in which case the appropriate transformation is selected. See [`∞`](@ref).

Some common transformations are predefined as constants, see [`asℝ`](@ref), [`asℝ₋`](@ref), [`asℝ₊`](@ref), [`as𝕀`](@ref).

!!! note
    The finite arguments are promoted to a common type and affect promotion. Eg `transform(as(0, ∞), 0f0) isa Float32`, but `transform(as(0.0, ∞), 0f0) isa Float64`.

