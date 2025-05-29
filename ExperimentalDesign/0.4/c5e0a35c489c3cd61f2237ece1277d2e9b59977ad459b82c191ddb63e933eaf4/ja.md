```julia
DesignDistribution(
    factors::NamedTuple
) -> ExperimentalDesign.DesignDistribution

```

```jldoctest
julia> DesignDistribution((f1 = Uniform(2, 3), f2 = DiscreteUniform(-1, 5), f3 = Uniform(5, 10)))
DesignDistribution
Formula: 0 ~ f1 + f2 + f3
Factor Distributions:
f1: Uniform{Float64}(a=2.0, b=3.0)
f2: DiscreteUniform(a=-1, b=5)
f3: Uniform{Float64}(a=5.0, b=10.0)

```
