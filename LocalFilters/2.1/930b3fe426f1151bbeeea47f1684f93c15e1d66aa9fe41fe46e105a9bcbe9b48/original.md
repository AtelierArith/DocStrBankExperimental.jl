```
strel(T, A)
```

yields a *structuring element* suitable for mathematical morphology operations. The result is an array whose elements have type `T` (which can be `Bool` or a floating-point type). Argument `A` can be a hyper-rectangular Cartesian sliding window or an array with boolean elements.

If `T` is a floating-point type, then the result is a so-called *flat* structuring element whose coefficients are `zero(T)` inside the shape defined by `A` and `-T(Inf)` elsewhere.

See also [`LocalFilters.kernel`](@ref), [`LocalFilters.box`](@ref), and [`LocalFilters.ball`](@ref).
