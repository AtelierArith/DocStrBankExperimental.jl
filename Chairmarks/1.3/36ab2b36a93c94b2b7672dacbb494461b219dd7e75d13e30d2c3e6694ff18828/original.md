Chairmarks provides the macros [`@b`](@ref) and [`@be`](@ref) for benchmarking code. See their respective docstrings for usage.

```julia
julia> @b evalpoly(rand(), rand(100))
198.077 ns (2 allocs: 928 bytes)
```

Documentation: https://chairmarks.lilithhafner.com/stable

Tutorial: https://chairmarks.lilithhafner.com/stable/tutorial.html

Reference: see docstrings of [`@be`](@ref) and [`@b`](@ref)
