```julia
DesignDistribution(
    distribution::Distributions.Distribution,
    n::Int64
) -> ExperimentalDesign.DesignDistribution

```

```jldoctest
julia> DesignDistribution(DiscreteNonParametric([-1, 1], [0.5, 0.5]), 6)
DesignDistribution
Formula: 0 ~ factor1 + factor2 + factor3 + factor4 + factor5 + factor6
Factor Distributions:
factor1: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])
factor2: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])
factor3: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])
factor4: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])
factor5: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])
factor6: DiscreteNonParametric{Int64, Float64, Vector{Int64}, Vector{Float64}}(support=[-1, 1], p=[0.5, 0.5])

```
