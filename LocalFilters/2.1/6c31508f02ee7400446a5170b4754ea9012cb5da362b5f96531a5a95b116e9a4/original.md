```
LocalFilters.kernel_range([ord=FORWARD_FILTER,] rng::AbstractRange{<:Integer})
LocalFilters.kernel_range([ord=FORWARD_FILTER,] len::Integer)
LocalFilters.kernel_range([ord=FORWARD_FILTER,] start::Integer, stop::Integer)
```

yield an unit-step `Int`-valued index range based on range `rng`, dimension length `len`, or first and last indices `start` and `stop`. In the case of a given dimension length, a centered range of this length is returned (for even lengths, the same conventions as in `fftshift` are used).

If ordering `ord` is specified, the returned range is suitable for this ordering.

See also [`LocalFilters.kernel`](@ref), [`LocalFilters.centered_offset`](@ref), and [`LocalFilters.centered`](@ref).
