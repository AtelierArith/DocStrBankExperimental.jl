```
logprior(model::Model, chain::AbstractMCMC.AbstractChains)
```

MCMC `chain` の各サンプルで評価された対数事前確率の配列を返します。

# 例

```jldoctest
julia> using MCMCChains, Distributions

julia> @model function demo_model(x)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, sqrt(s))
           for i in eachindex(x)
               x[i] ~ Normal(m, sqrt(s))
           end
       end;

julia> # MCMCChains を使用してサンプルのチェーンを構築
       chain = Chains(rand(10, 2, 3), [:s, :m]);

julia> logprior(demo_model([1., 2.]), chain);
```
