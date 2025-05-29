```
function randformula(
    [T::Type{<:Formula}=SyntaxTree,]
    [rng::Union{Integer,AbstractRNG}=Random.GLOBAL_RNG,]
    maxheight::Integer,
    alphabet::Union{AbstractVector,AbstractAlphabet},
    operators::AbstractVector{<:Operator},
    args...;
    maxmodaldepth::Integer=maxheight,
    atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}=randatom,
    opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}=nothing,
    alphabet_sample_kwargs::Union{Nothing,AbstractVector}=nothing,
    kwargs...
)
```

Return a pseudo-randomic formula of type [`T`](@ref).

# Arguments

  * `rng::Union{Intger,AbstractRNG}=Random.GLOBAL_RNG`: random number generator;
  * `maxheight::Integer`: maximum height of the generated structure;
  * `alphabet::AbstractAlphabet`: collection from which atoms are chosen randomly;
  * `operators::AbstractVector{<:Operator}`: vector from which legal operators are chosen.

# Keyword Arguments

  * `maxmodaldepth::Integer`: maximum modal depth;
  * `atompicker::Union{Nothing,Function,AbstractWeights,AbstractVector{<:Real}}`: method used   to pick a random element. For example, this could be Base.rand, StatsBase.sample or   an array of integers or an array of `StatsBase.AbstractWeights`;
  * `opweights::Union{Nothing,AbstractWeights,AbstractVector{<:Real}}`: operators are sampled   with probabilities proportional to this vector (see [`AbstractWeights`](@ref) of   StatsBase package).
  * `alphabet_sample_kwargs::AbstractVector`: pool of atoms to pull from if the given alphabet   is not finite.
  * `basecase::Function` = method to specify the base case of the recursion; if not specified,   it returns `atompicker`.

[!WARNING] The basecase is applied at the end of the recustion (i.e., when height = 0). If introducting a basecase which produces a subformula, please adjust the `maxheight` parameter value accordingly (e.g., when producing a subformula of the type o(p,q), where `o` is a connective and `p,q` are atoms, to generate a formula of maxheight `n` provide a value of `n-1` for the `maxheight` parameter).

  * `mode::Bool = :maxheight` constrains the generated syntax tree   to having a height smaller or equal to `maxheight` (`mode = :maxheight`),   to having height equal to `maxheight` (`mode = :exactheight`),   or to having height equal to `maxheight` and being full (`mode = :full`),.
  * `earlystoppingtreshold::Float` : when `mode = :maxheight`,   controls the probability of calling the basecase before reaching.

# Examples

```julia-repl
julia> syntaxstring(randformula(4, ExplicitAlphabet([1,2]), [NEGATION, CONJUNCTION, IMPLICATION]))
"¬((¬(¬(2))) → ((1 → 2) → (1 → 2)))"
```

See also [`AbstractAlphabet`](@ref), [`AbstractWeights`](@ref), [`Atom`](@ref), [`Operator`](@ref), [`SyntaxBranch`](@ref), [`SyntaxTree`](@ref).
