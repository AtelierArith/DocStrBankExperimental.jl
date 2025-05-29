```
BSplineBasis{T<:AbstractVector{<:Real}}
```

Type for a B-spline basis with breakpoint vector of type `T`.

Here, a B-spline basis is completely specified by its order $k$ and breakpoint sequence. The knot sequence is derived from the breakpoint sequence by duplicating the first and last breakpoints so they each appear $k$ times. Knot sequences where the first and last breakpoints do not appear $k$ times are not supported by this data type.

!!! note
    Here, unlike in some other B-spline libraries, $k$ always refers to the *order* of a B-spline, not its *degree* (order = degree + 1).

