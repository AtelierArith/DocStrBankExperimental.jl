```
randatom(
    [rng::Union{Random.AbstractRNG,Integer},]
    a::AbstractAlphabet,
    args...;
    kwargs...
)
```

Randomly generate an [`Atom`](@ref) from a *finite* [`AbstractAlphabet`](@ref) according to a uniform distribution.

# Examples

```julia-repl
julia> alphabet = ExplicitAlphabet(1:5)
ExplicitAlphabet{Int64}(Atom{Int64}[Atom{Int64}: 1, Atom{Int64}: 2, Atom{Int64}: 3, Atom{Int64}: 4, Atom{Int64}: 5])

julia> randatom(42, alphabet)
Atom{Int64}: 4
```

See also [`natoms`](@ref), [`AbstractAlphabet`](@ref).
