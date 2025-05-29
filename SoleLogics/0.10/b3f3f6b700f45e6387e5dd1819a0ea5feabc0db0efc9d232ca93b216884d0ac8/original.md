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

# Implementation

If you use [`interpret`](@ref) function and you pass a [`DefaultedTruthDict`](@ref) as [`AbstractAssignment`](@ref)  and the [`Atom`](@ref) is not present in the dictionary, then the default dictionary value will be  returned and not the [`Atom`](@ref) itself.

Here is an example of this.

```julia-repl
julia> interpret(Atom(5), DefaultedTruthDict(string.(1:4), false))
⊥
```

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

See also [`AbstractAssignment`](@ref), [`AbstractInterpretation`](@ref), [`interpret`](@ref), [`Atom`](@ref), [`TruthDict`](@ref), [`DefaultedTruthDict`](@ref).
