```
convert(::Type{ProjectorPoint}, ::Stiefelpoint)
```

Convert a point `p` on [`Stiefel`](@ref) that also represents a point (i.e. subspace) on [`Grassmann`](@ref) to a projector representation of said subspace, i.e. compute the [`canonical_project!`](@ref) for

$$
  π^{\mathrm{SG}}(p) = pp^{\mathrm{T}}.
$$
