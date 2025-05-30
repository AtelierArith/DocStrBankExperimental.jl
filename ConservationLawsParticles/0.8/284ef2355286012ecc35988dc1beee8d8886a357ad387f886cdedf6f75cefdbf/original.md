```
pwc_densities!(dens, xs::AbstractVector{<:Real}...)
pwc_densities!(dens, xs::Tuple{Vararg{AbstractVector{<:Real}}})
```

This is an inplace version of [`pwc_densities`](@ref) that writes the result in `dens`.

See the documentation of [`pwc_densities`](@ref) for an explanation.
