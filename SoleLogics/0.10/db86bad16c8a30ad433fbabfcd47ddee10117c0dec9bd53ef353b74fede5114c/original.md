```
struct TruthDict{D<:AbstractDict{A where A<:Atom,T where T<:Truth}} <: AbstractAssignment
    truth::D
end
```

A logical interpretation instantiated as a dictionary, explicitly assigning truth values to a *finite* set of atoms.

# Examples

```julia-repl
julia> TruthDict(1:4)
TruthDict with values:
┌────────┬────────┬────────┬────────┐
│      4 │      2 │      3 │      1 │
│  Int64 │  Int64 │  Int64 │  Int64 │
├────────┼────────┼────────┼────────┤
│      ⊤ │      ⊤ │      ⊤ │      ⊤ │
└────────┴────────┴────────┴────────┘


julia> t1 = TruthDict(1:4, false); t1[5] = true; t1
TruthDict with values:
┌───────┬───────┬───────┬───────┬───────┐
│     5 │     4 │     2 │     3 │     1 │
│ Int64 │ Int64 │ Int64 │ Int64 │ Int64 │
├───────┼───────┼───────┼───────┼───────┤
│     ⊤ │     ⊥ │     ⊥ │     ⊥ │     ⊥ │
└───────┴───────┴───────┴───────┴───────┘

julia> t2 = TruthDict(["a" => true, "b" => false, "c" => true])
TruthDict with values:
┌────────┬────────┬────────┐
│      c │      b │      a │
│ String │ String │ String │
├────────┼────────┼────────┤
│      ⊤ │      ⊥ │      ⊤ │
└────────┴────────┴────────┘

julia> check(parseformula("a ∨ b"), t2)
true

```

!!! note
    If prompted for the value of an unknown atom, this throws an error. If boolean, integer, or float values are specified, they are converted to `Truth` values. If the structure is initialized as empty, [`BooleanTruth`](@ref) values are assumed.


See also [`AbstractAssignment`](@ref),  [`AbstractInterpretation`](@ref), [`DefaultedTruthDict`](@ref), [`BooleanTruth`](@ref).
