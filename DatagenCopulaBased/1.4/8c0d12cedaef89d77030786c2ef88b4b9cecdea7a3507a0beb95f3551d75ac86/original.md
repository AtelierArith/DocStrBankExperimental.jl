```
MarshallOlkinCopula
```

Fields:

  * n::Int - number of marginals
  * λ::Vector{Real} - vector of non-negative parameters λₛ, i.e.:   λ = [λ₁, λ₂, ..., λₙ, λ₁₂, λ₁₃, ..., λ₁ₙ, λ₂₃, ..., λₙ₋₁ₙ, λ₁₂₃, ..., λ₁₂...ₙ]   and n = ceil(Int, log(2, length(λ)-1)).

Constructor

```
MarshallOlkinCopula(λ)
```

length(λ) ≧ 3 is required

```jldoctest
julia> MarshallOlkinCopula([0.5, 0.5, 0.6])
MarshallOlkinCopula(2, [0.5, 0.5, 0.6])

julia> MarshallOlkinCopula([0.5, 0.5, 0.6, 0.7, 0.7, 0.7, 0.8])
MarshallOlkinCopula(3, [0.5, 0.5, 0.6, 0.7, 0.7, 0.7, 0.8])
```
