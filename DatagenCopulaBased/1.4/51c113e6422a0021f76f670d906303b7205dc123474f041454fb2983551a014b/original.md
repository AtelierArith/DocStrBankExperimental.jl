```
ChainFrechetCopulas
```

Chain of bi-variate Frechet copulas. Models each subsequent pair of marginals by the bi-variate Frechet copula.

Fields:     - n::Int - number of marginals     - α::Vector{Real}  - vector of parameters for the maximal copula     - β::Vector{Real} - vector of parameters for the minimal copula

Here α[i] and β[i] parameterized bi-variate Frechet copula between i th and i+1 th marginals.

Constructors

```
ChainFrechetCopulas(α::Vector{Real})
```

here β = zero(0)

```
ChainFrechetCopulas(α::Vector{Real}, β::Vector{Real})
```

```jldoctest
julia> ChainFrechetCopulas([0.2, 0.3, 0.4])
ChainFrechetCopulas(4, [0.2, 0.3, 0.4], [0.0, 0.0, 0.0])

julia> ChainFrechetCopulas([0.2, 0.3, 0.4], [0.1, 0.1, 0.1])
ChainFrechetCopulas(4, [0.2, 0.3, 0.4], [0.1, 0.1, 0.1])
```
