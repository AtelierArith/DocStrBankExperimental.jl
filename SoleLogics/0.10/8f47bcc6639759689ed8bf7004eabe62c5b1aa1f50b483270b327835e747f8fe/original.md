```
abstract type SyntaxStructure <: Formula end
```

Abstract type for the purely-syntactic component of a logical formula (e.g., no fancy memoization structure associated). The typical representation is the [`SyntaxTree`](@ref), however, different implementations can cover specific syntactic forms (e.g., [conjunctive](https://en.wikipedia.org/wiki/Conjunctive_normal_form) or [disjunctive](https://en.wikipedia.org/wiki/Disjunctive_normal_form) normal forms).

# Interface

  * See also [`Formula`](@ref)

See also [`Formula`](@ref), [`AbstractLogic`](@ref), [`SyntaxTree`](@ref), [`tree`](@ref).
