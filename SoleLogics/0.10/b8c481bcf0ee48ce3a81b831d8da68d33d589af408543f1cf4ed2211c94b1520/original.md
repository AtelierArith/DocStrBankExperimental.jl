```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    height::Integer,
    alphabet::Union{AbstractVector,AbstractAlphabet},
    operators::AbstractVector{<:Operator},
    args...;
    modaldepth::Integer=height,
    atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}=randatom,
    opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing,
    alphabet_sample_kwargs::Union{Nothing,AbstractVector}=nothing,
    kwargs...
)
```

Return a pseudo-randomic formula of type [`T`](@ref).

# Arguments

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: random number generator;
  * `height::Integer`: height of the generated structure;
  * `alphabet::AbstractAlphabet`: collection from which atoms are chosen randomly;
  * `operators::AbstractVector{<:Operator}`: vector from which legal operators are chosen.

# Keyword Arguments

  * `modaldepth::Integer`: maximum modal depth;
  * `atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}`: method used   to pick a random element. For example, this could be Base.rand, StatsBase.sample or   an array of integers or an array of `StatsBase.AbstractWeights`;
  * `opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}`: operators are sampled   with probabilities proportional to this vector (see [`AbstractWeights`](@ref) of   StatsBase package).
  * `alphabet_sample_kwargs::AbstractVector`: pool of atoms to pull from if the given alphabet   is not finite.

# Examples

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

See also [`AbstractAlphabet`](@ref), [`AbstractWeights`](@ref), [`Atom`](@ref), [`Operator`](@ref), [`SyntaxBranch`](@ref), [`SyntaxTree`](@ref).
