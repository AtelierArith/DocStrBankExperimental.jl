```
project(m::BiCM;   α::Float64=0.05, layer::Symbol=:bottom, precomputed::Bool=true, 
                    distribution::Symbol=:Poisson, adjustment::PValueAdjustment=BenjaminiHochberg(),
                        multithreaded::Bool=false)
```

Obtain the statistically validated projected graph of the BiCM model `m` onto the layer `layer` using the V-motifs and the significance level `α` combined with the p-value adjustment method `adjustment`.

# Arguments

  * `α`: the significance level.
  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`.
  * `precomputed`: if true, the expected values of the biadjacency matrix are used, otherwise the parameters are computed from the model parameters.
  * `distribution`: the distribution used to compute the p-values. This can be `:Poisson` or `:PoissonBinomial`.
  * `adjustment`: the method used to adjust the p-values for multiple testing. This can be any of the methods in the `PValueAdjustment` type (see `MultipleTesting.jl`). By default, the Benjamini-Hochberg method is used.
  * `multithreaded`: if true, the p-values are computed using multithreading.

# Examples

```jldoctest project_bicm
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> project(model, layer=:bottom)
{25, 0} undirected simple Int64 graph

```

```jldoctest project_bicm
julia> project(model, layer=:top)
{15, 0} undirected simple Int64 graph

```
