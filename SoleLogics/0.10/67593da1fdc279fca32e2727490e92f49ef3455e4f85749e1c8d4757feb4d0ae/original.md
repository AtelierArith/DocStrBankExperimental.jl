```
randatom(
    [rng::Union{Random.AbstractRNG,Integer},]
    a::UnionAlphabet;
    atompicking_mode::Symbol=:uniform,
    subalphabets_weights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing
)::Atom
```

Sample an atom from a `UnionAlphabet`. By default, the sampling is uniform with respect to the atoms.

By setting `atompicking_mode = :uniform_subalphabets` one can force a uniform sampling with respect to the sub-alphabets.

Moreover, one can specify a `:weighted` `atompicking_mode`, together with a `subalphabets_weights` vector.

# Examples

```julia-repl
julia> alphabet1 = ExplicitAlphabet(Atom.(1:10));
julia> alphabet2 = ExplicitAlphabet(Atom.(11:20));
julia> union_alphabet = UnionAlphabet([alphabet1, alphabet2]);

julia> randatom(42, union_alphabet)
Atom{Int64}: 11

julia> randatom(42, union_alphabet; atompicking_mode=:uniform_subalphabets)
Atom{Int64}: 11

julia> for i in 1:10
            randatom(
                union_alphabet;
                atompicking_mode=:weighted,
                subalphabets_weights=[0.8,0.2]
            ) |> syntaxstring |> vcat |> print
        end
["6"]["3"]["10"]["7"]["2"]["2"]["6"]["9"]["20"]["16"]
```

See also [`UnionAlphabet`](@ref).
