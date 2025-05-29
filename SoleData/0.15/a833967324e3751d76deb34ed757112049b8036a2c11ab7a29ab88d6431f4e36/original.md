```
struct MultiFormula{F<:Formula} <: AbstractSyntaxStructure
    modforms::Dict{Int,F}
end
```

A symbolic antecedent that can be checked on a `MultiLogiset`, associating antecedents to modalities.
