```
struct DefaultedTruthDict{
    D<:AbstractDict{A where A<:Atom,T where T<:Truth},
    T<:Truth
} <: AbstractAssignment
    truth::D
    default_truth::T
end
```

A truth table instantiated as a dictionary, plus a default value. This structure assigns truth values to a set of atoms and, when prompted for the value of an atom that is not in the dictionary, it returns `default_truth`.

# Examples

```julia-repl
julia> t1 = DefaultedTruthDict(string.(1:4), false); t1["5"] = false; t1
DefaultedTruthDict with default truth `⊥` and values:
┌────────┬────────┬────────┬────────┬────────┐
│      4 │      1 │      5 │      2 │      3 │
│ String │ String │ String │ String │ String │
├────────┼────────┼────────┼────────┼────────┤
│      ⊤ │      ⊤ │      ⊥ │      ⊤ │      ⊤ │
└────────┴────────┴────────┴────────┴────────┘

julia> check(parseformula("1 ∨ 2"), t1)
true

julia> check(parseformula("1 ∧ 5"), t1)
false

```

See also [`TruthDict`](@ref), [`AbstractAssignment`](@ref), [`AbstractInterpretation`](@ref).
