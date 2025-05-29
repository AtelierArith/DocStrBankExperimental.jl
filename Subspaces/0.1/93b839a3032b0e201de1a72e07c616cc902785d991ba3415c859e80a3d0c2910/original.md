```julia
variable_in_space(
    S::Subspaces.Subspace{<:Real, N}
) -> Union{Convex.MultiplyAtom, Convex.ReshapeAtom}

```

Creates a `Convex.jl` variable ranging over the given subspace.
