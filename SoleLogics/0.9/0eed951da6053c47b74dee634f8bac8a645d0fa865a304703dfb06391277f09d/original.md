```
check(
    φ::Formula,
    i::AbstractInterpretation,
    args...;
    kwargs...
)::Bool
```

Check a formula on a logical interpretation (or model), returning `true` if the truth value for the formula `istop`. This process is referred to as (finite) [model checking](https://en.wikipedia.org/wiki/Model_checking), and there are many algorithms for it, typically depending on the complexity of the logic.

# Examples

```julia-repl
julia> @atoms String p q
2-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")

julia> td = TruthDict([p => TOP, q => BOT])
TruthDict with values:
┌────────┬────────┐
│      q │      p │
│ String │ String │
├────────┼────────┤
│      ⊥ │      ⊤ │
└────────┴────────┘

julia> check(CONJUNCTION(p,q), td)
false
```

See also [`interpret`](@ref), [`Formula`](@ref), [`AbstractInterpretation`](@ref), [`TruthDict`](@ref).
