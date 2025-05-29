```
struct MultiFormula{F<:Formula} <: AbstractSyntaxStructure
    modforms::Dict{Int,F}
end
```

A logical formula that can be checked on a `MultiLogiset`, representing the logical and between formulas across different modalities.

See also [`MultiLogiset`](@ref), [`eachmodality`](@ref), [`nmodalities`](@ref), [`modforms`](@ref).
