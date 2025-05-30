```
pwc_densities(xs::AbstractVector{<:Real}...)
pwc_densities(xs::Tuple{Vararg{AbstractVector{<:Real}}})
```

Given a list of `n` families of particles of lengths `l₁, …, lₙ`, returns an `n`-tuple whose `s`-th entry is an `n×2×lₛ` array `densₛ`.

This array contains the information about the densities of all the species around the particles of the `s`-th species. This array is indexed as `[o,side,i]`, where `o∈{1, …, n}` is the index of the other species whose density we want to know, `side` is either `1` if we want to know the left density or `2` for the right density, and `i∈{1, …, lₛ}` is the index of the particle.

In other words, `densₛ[o,side,i]` is the density of the `o`-th species on the left (`side=1`) or right (`side=2`) of the `i`-th particle of the `s`-th species.

See also [`pwc_densities!`](@ref) for an inplace version.

# Examples

```jldoctest
julia> pwc_densities([0,1,2], [0,2,3])
([0.0 0.5; 0.0 0.25;;; 0.5 0.5; 0.25 0.25;;; 0.5 0.0; 0.25 0.5], [0.0 0.5; 0.0 0.25;;; 0.5 0.0; 0.25 0.5;;; 0.0 0.0; 0.5 0.0])
```
