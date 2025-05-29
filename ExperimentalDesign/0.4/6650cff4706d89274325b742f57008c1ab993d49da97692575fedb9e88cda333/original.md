```julia
DesignDistribution(
    factors::Array
) -> ExperimentalDesign.DesignDistribution

```

```jldoctest
julia> DesignDistribution([Uniform(2, 3), DiscreteUniform(-1, 5), Uniform(5, 10)])
DesignDistribution
Formula: 0 ~ factor1 + factor2 + factor3
Factor Distributions:
factor1: Uniform{Float64}(a=2.0, b=3.0)
factor2: DiscreteUniform(a=-1, b=5)
factor3: Uniform{Float64}(a=5.0, b=10.0)

```
