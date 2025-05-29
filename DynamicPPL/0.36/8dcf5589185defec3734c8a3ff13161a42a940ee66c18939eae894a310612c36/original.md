```
logjoint(model::Model, chain::AbstractMCMC.AbstractChains)
```

Return an array of log joint probabilities evaluated at each sample in an MCMC `chain`.

# Examples

```jldoctest
julia> using MCMCChains, Distributions

julia> @model function demo_model(x)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, sqrt(s))
           for i in eachindex(x)
               x[i] ~ Normal(m, sqrt(s))
           end
       end;

julia> # construct a chain of samples using MCMCChains
       chain = Chains(rand(10, 2, 3), [:s, :m]);

julia> logjoint(demo_model([1., 2.]), chain);
```
