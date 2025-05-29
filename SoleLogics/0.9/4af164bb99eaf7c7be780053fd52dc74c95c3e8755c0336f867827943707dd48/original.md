```
randformula(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG, ]
    height::Integer,
    alphabet,
    operators::AbstractVector;
    kwargs...
)::SyntaxTree

randformula(
    [rng::Union{Integer,AbstractRNG} = Random.GLOBAL_RNG, ]
    height::Integer,
    g::AbstractGrammar;
    kwargs...
)::SyntaxTree
```

Return a pseudo-randomic `SyntaxTree`.

# Arguments

  * `rng::Union{Intger,AbstractRNG} = Random.GLOBAL_RNG`: random number generator;
  * `height::Integer`: height of the generated structure;
  * `alphabet::AbstractAlphabet`: collection from which atoms are chosen randomly;
  * `operators::AbstractVector`: vector from which legal operators are chosen;
  * `g::AbstractGrammar`: alternative to passing alphabet and operators separately. (TODO explain?)

# Keyword Arguments

  * `modaldepth::Integer`: maximum modal depth
  * `atompicker::Function`: method used to pick a random element. For example, this could be   Base.rand or StatsBase.sample.
  * `opweights::AbstractWeights`: weight vector over the set of operators (see `StatsBase`).

# Examples

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

See also [`AbstractAlphabet`](@ref), [`SyntaxBranch`](@ref).
