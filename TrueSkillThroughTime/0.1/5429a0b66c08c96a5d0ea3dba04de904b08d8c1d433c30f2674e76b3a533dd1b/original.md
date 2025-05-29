The `History` class

```
History(composition::Vector{Vector{Vector{String}}},
results::Vector{Vector{Float64}}=Vector{Vector{Float64}}(),
times::Vector{Int64}=Int64[], priors::Dict{String,Player}=Dict{String,Player}()
; mu::Float64=MU, sigma::Float64=SIGMA, beta::Float64=BETA,
gamma::Float64=GAMMA, p_draw::Float64=P_DRAW, online::Bool=false,
weights::Vector{Vector{Vector{Float64}}}=Vector{Vector{Vector{Float64}}}())
```

Properties:

```
size::Int64
batches::Vector{Batch}
agents::Dict{String,Agent}
time::Bool
mu::Float64
sigma::Float64
beta::Float64
gamma::Float64
p_draw::Float64
online::Bool
```
