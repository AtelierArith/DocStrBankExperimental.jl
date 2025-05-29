```
struct Rule{O} <: AbstractModel{O}
    antecedent::Formula
    consequent::M where {M<:AbstractModel{<:O}}
    info::NamedTuple
end
```

A `Rule` is one of the fundamental building blocks of symbolic modeling, and has the semantics:

```
IF (antecedent) THEN (consequent) END
```

where the [`antecedent`](@ref) is a formula to be checked, and the [`consequent`](@ref) is the local outcome of the block.

# Examples

```julia-repl
julia> Rule(CONJUNCTION(Atom("p"), Atom("q")), ConstantModel(2))
▣ (p) ∧ (q)  ↣  2
```

See also [`AbstractModel`](@ref), [`antecedent`](@ref), [`consequent`](@ref), `SoleLogics.Formula`.
