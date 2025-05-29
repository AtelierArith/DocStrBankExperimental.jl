```julia
collocation_matrix(basis)
collocation_matrix(basis, x)

```

Convenience function to obtain a “collocation matrix” at points `x`, which is assumed to have a concrete `eltype`. The default is `x = grid(basis)`, specialized methods may exist for this when it makes sense.

The collocation matrix may not be an `AbstractMatrix`, all it needs to support is `C \ y` for compatible vectors `y = f.(x)`.

Methods are type stable. The elements of `x` can be derivatives, see [`𝑑`](@ref).
