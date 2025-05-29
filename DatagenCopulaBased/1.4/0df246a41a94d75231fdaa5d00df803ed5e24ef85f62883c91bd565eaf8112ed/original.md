```
ChainArchimedeanCopulas
```

Subsequent pairs of marginals are modeled by bi-variate copulas form the Archimedean family, following copulas are supported: "Clayton", "Frank", "Ali-Mikhail-Haq", "Gumbel" copula is not supported.

Fields:

  * n::Int - number of variables
  * θ::Vector{Real} - a vector of parameters
  * copulas::Vector{String} - a vector indicating bi-variate copulas.

possible elements "clayton", "frank", "amh"

Constructor

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::Vector{String})
```

requires length(θ) = length(copulas) and limitations on θ for particular bi-variate copulas

Constructor

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::String)
```

one copula family for all subsequent pairs of marginals.

Constructors

```
ChainArchimedeanCopulas(θ::Vector{Real}, copulas::Vector{String}, cor::Type{<:CorrelationType})

ChainArchimedeanCopulas(θ::Vector{Real}, copulas::String, cor::Type{<:CorrelationType})
```

For computing copula parameters from expected correlation use empty type cor::Type{<:CorrelationType}. cor ∈ {SpearmanCorrelation, KendallCorrelation} uses these correlations in the place of θ  in the constructor to compute θ.

In all cases n = length(θ)+1.

```jldoctest

julia> c = ChainArchimedeanCopulas([4., 11.], "frank")
ChainArchimedeanCopulas(3, [4.0, 11.0], ["frank", "frank"])

julia> c = ChainArchimedeanCopulas([.5, .7], ["frank", "clayton"], "Kendall")
ChainArchimedeanCopulas(3, [5.736282707019972, 4.666666666666666], ["frank", "clayton"])

```
