```
BerryCurvature(reciprocalspace::ReciprocalSpace, method::BerryCurvatureMethod)
BerryCurvature(reciprocalspace::ReciprocalSpace, μ::Real, d::Real=0.1, kx::T=nothing, ky::T=nothing) where {T<:Union{Nothing, Vector{Float64}}}
BerryCurvature(reciprocalspace::Union{BrillouinZone, ReciprocalZone}, bands::AbstractVector{Int}, abelian::Bool=true)
```

Construct a `BerryCurvature`.
