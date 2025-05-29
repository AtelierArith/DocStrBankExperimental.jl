```
rand([rng::AbstractRNG,]
      net::HybridNetwork,
      params::ParamsProcess,
      checkpreorder::Bool=true)
```

Simulate traits on `net` using the parameters `params`. For now, only parameters of type [`ParamsBM`](@ref) (univariate Brownian Motion) and [`ParamsMultiBM`](@ref) (multivariate Brownian motion) are accepted.

The simulation using a recursion from the root to the tips of the network, therefore, a pre-ordering of nodes is needed. If `checkpreorder=true` (default), [`PhyloNetworks.preorder!`](@extref) is called on the network beforehand. Otherwise, it is assumed that the preordering has already been calculated.

Returns an object of type [`TraitSimulation`](@ref), which has a matrix with the trait expectations and simulated trait values at all the nodes.

See examples below for accessing expectations and simulated trait values.

# Examples

## Univariate

```jldoctest randdoc
julia> phy = readnewick("(A:2.5,((U:1,#H1:0.5::0.4):1,(C:1,(D:0.5)#H1:0.5::0.6):1):0.5);");

julia> par = ParamsBM(1, 0.1) # BM with expectation 1 and variance 0.1.
ParamsBM:
Parameters of a BM with fixed root:
mu: 1.0
Sigma2: 0.1


julia> sim = rand(phy, par) # simulate along the network
TraitSimulation:
Trait simulation results on a network with 4 tips, using a BM model, with parameters:
mu: 1.0
Sigma2: 0.1
```

Below, we re-run the same simulation but with our own fixed random number generator for reproducibility.

```jldoctest randdoc
julia> # using Pkg; Pkg.add("StableRNGs") # to install StableRNGs if not done earlier

julia> using StableRNGs; rng = StableRNG(791); # for reproducibility

julia> sim = rand(rng, phy, par); # re-simulate

julia> traits = sim[:tips] # extract simulated values at the tips.
4-element Vector{Float64}:
 0.5991561486238962
 0.861066346792992
 1.367634062992289
 1.6439310845929571

julia> tiplabels(sim) # name of tips, in the same order as values above
4-element Vector{String}:
 "A"
 "U"
 "C"
 "D"
```

So, for example, the simulated trait value for taxon U (listed second) is ~0.86. For some purposes, we might want to access the values simulated at internal nodes, or at all nodes at once:

```jldoctest randdoc
julia> traits = sim[:internalnodes] # extract simulated values at internal nodes. Order: as in sim.M.internalnodenumbers
5-element Vector{Float64}:
 1.0716684901027937
 1.6007823049044083
 1.6756374575490327
 1.2194286026283034
 1.0

julia> traits = sim[:all] # simulated values at all nodes, ordered as in sim.M.nodenumbers_toporder
9-element Vector{Float64}:
 1.0
 1.2194286026283034
 1.6756374575490327
 1.367634062992289
 1.0716684901027937
 1.6007823049044083
 1.6439310845929571
 0.861066346792992
 0.5991561486238962
```

We might also want to extract the expected mean values (without noise). This is not very interesting under a standard BM model, but may become interesting under more complex models (e.g. with shifts). We can do so with an extra `:exp` index:

```jldoctest randdoc
julia> traits = sim[:tips, :exp] # expected values at the tips (also works for sim[:all, :exp] and sim[:internalnodes, :exp]).
4-element Vector{Float64}:
 1.0
 1.0
 1.0
 1.0
```

## Multivariate

```jldoctest randdoc
julia> phy = readnewick("(A:2.5,((B:1,#H1:0.5::0.4):1,(C:1,(V:0.5)#H1:0.5::0.6):1):0.5);");

julia> par = ParamsMultiBM([1.0, 2.0], [1.0 0.5; 0.5 1.0]) # BM with expectation [1.0, 2.0] and variance [1.0 0.5; 0.5 1.0].
ParamsMultiBM:
Parameters of a MBD with fixed root:
mu: [1.0, 2.0]
Sigma: [1.0 0.5; 0.5 1.0]

julia> using StableRNGs; rng = StableRNG(9851); # for reproducibility

julia> sim = rand(rng, phy, par) # simulate on the phylogeny
TraitSimulation:
Trait simulation results on a network with 4 tips, using a MBD model, with parameters:
mu: [1.0, 2.0]
Sigma: [1.0 0.5; 0.5 1.0]


julia> traits = sim[:tips] # extract simulated values at the tips (each column contains the simulated traits for one node).
2×4 Matrix{Float64}:
 3.8013    0.839485  0.346092  1.91131
 5.91725  -0.59143   0.458569  0.629048
```

The 2 rows to the 2 correlated traits and the columns correspond to the 4 taxa (tips). The order in which taxa are listed is obtained with `tiplabels`:

```jldoctest randdoc
julia> tiplabels(sim)
4-element Vector{String}:
 "A"
 "B"
 "C"
 "V"
```

As in the univariate case, we can also extract the values simulated at internal nodes, or all nodes (but listed in preorder), or expected mean values.

```jldoctest randdoc
julia> sim[:internalnodes] # simulated values at internal nodes. order: same as in sim.M.internalnodenumbers
2×5 Matrix{Float64}:
 -0.604224  0.755722  2.14755  0.484292  1.0
 -0.338922  0.373921  1.15174  0.695561  2.0

julia> traits = sim[:all]; # 2×9 Matrix: values at all nodes, ordered as in sim.M.nodenumbers_toporder

julia> sim[:tips, :exp] # expected values (also works for sim[:all, :exp] and sim[:internalnodes, :exp])
2×4 Matrix{Float64}:
 1.0  1.0  1.0  1.0
 2.0  2.0  2.0  2.0
```
