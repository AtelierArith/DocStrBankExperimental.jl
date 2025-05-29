```
descendencedataframe(net::HybridNetwork, which=:allhybrids; checkpreorder=true)
descendencedataframe(net::HybridNetwork, node::Vector{Node}; checkpreorder=true)
descendencedataframe(net::HybridNetwork, edge::Vector{Edge}; checkpreorder=true)
```

Data frame containing the genomic proportion inherited by each taxon in `net`, from each hybrid node by default in the first method, or from each node or edge in the input vector in the second and third methods. The data frame has 1 row per tip (taxon) in the network and the following columns:

  * 1 column per edge or node, with columns named according to the pattern shift*{edge*number}" where `edge_number` is the number of the edge associated with an input edge or node (in which case the parent edge is used)
  * 1 additional column labeled `tipnames`, containing the tip labels.

The `shift_*` columns in this data frame can be used as regressor vectors associated with shifts on input `edge`s or on edges that are above input `node`s. With option `which=:allhybrids` in last method, each shift column is associated with a hybrid node in `net`, to model a shift on the edge that is immediately below the hybrid node. This can be used to test for transgressive evolution: see examples below.

These methods use [`PhyloNetworks.descendencematrix`](@extref), so `net` might be modified to store a vector of its nodes sorted in a pre-order.

# Examples

```jldoctest descendence
julia> net = readnewick("(A:2.5,((B:1,#H1:0.5::0.4):1,(C:1,(D:0.5)#H1:0.5::0.6):1):0.5);");

julia> preorder!(net)

julia> using PhyloPlots

julia> plot(net, shownodenumber=true); # to locate nodes

julia> nodes_shifts = indexin([1,-5], [n.number for n in net.node]) # Put a shift on edges ending at nodes 1 and -5
2-element Vector{Union{Nothing, Int64}}:
 1
 7

julia> params = ParamsBM(10, 0.1, ShiftNet(net.node[nodes_shifts], [3.0, -3.0],  net))
ParamsBM:
Parameters of a BM with fixed root:
mu: 10.0
Sigma2: 0.1

There are 2 shifts on the network:
──────────────────────────
  Edge Number  Shift Value
──────────────────────────
          8.0         -3.0
          1.0          3.0
──────────────────────────

julia> using Random; Random.seed!(2468); # sets the seed for reproducibility

julia> sim = rand(net, params); # simulate a dataset with shifts

julia> using DataFrames # to handle data frames

julia> dat = DataFrame(trait = sim[:tips], tipnames = sim.M.tipnames);

julia> dat = DataFrame(trait = [13.391976856737717, 9.55741491696386, 7.17703734817448, 7.889062527849697],
        tipnames = ["A","B","C","D"]) # hard-coded, to be independent of random number generator
4×2 DataFrame
 Row │ trait     tipnames 
     │ Float64   String   
─────┼────────────────────
   1 │ 13.392    A
   2 │  9.55741  B
   3 │  7.17704  C
   4 │  7.88906  D

julia> dfr_shift = descendencedataframe(net, net.node[nodes_shifts]) # the regressors matching the shifts.
4×3 DataFrame
 Row │ shift_1  shift_8  tipnames 
     │ Float64  Float64  String   
─────┼────────────────────────────
   1 │     1.0      0.0  A
   2 │     0.0      0.0  B
   3 │     0.0      1.0  C
   4 │     0.0      0.6  D

julia> dfr = innerjoin(dat, dfr_shift, on=:tipnames); # join data and regressors in a single dataframe

julia> using StatsModels # for statistical model formulas

julia> fitBM = phylolm(@formula(trait ~ shift_1 + shift_8), dfr, net; reml=false) # actual fit
PhyloNetworkLinearModel

Formula: trait ~ 1 + shift_1 + shift_8

Model: Brownian motion

Parameter Estimates, using ML:
phylogenetic variance rate: 0.0112618

Coefficients:
────────────────────────────────────────────────────────────────────────
                Coef.  Std. Error      t  Pr(>|t|)  Lower 95%  Upper 95%
────────────────────────────────────────────────────────────────────────
(Intercept)   9.48238    0.327089  28.99    0.0220    5.32632   13.6384
shift_1       3.9096     0.46862    8.34    0.0759   -2.04479    9.86399
shift_8      -2.4179     0.422825  -5.72    0.1102   -7.7904     2.95461
────────────────────────────────────────────────────────────────────────
Log Likelihood: 1.8937302027
AIC: 4.2125395947
```

Next we illustrate the model with heterosis, aka transgressive evolution: with a shift in the trait after successful hybridization. First how to simulated according to this model:

```jldoctest descendence
julia> nodes_hybrids = indexin([5], [n.number for n in net.node]); # Put a shift on edges below hybrids

julia> params = ParamsBM(10, 0.1, ShiftNet(net.node[nodes_hybrids], [3.0],  net));

julia> using Random; Random.seed!(2468); # sets the seed for reproducibility

julia> sim = rand(net, params); # simulate a dataset with shifts

julia> dat = DataFrame(trait = sim[:tips], tipnames = sim.M.tipnames);
```

and next how to analyze data under a transgressive evolution model. Below we hard-code data values for more reproducibility.

```jldoctest descendence
julia> dat = DataFrame(trait = [10.391976856737717, 9.55741491696386, 10.17703734817448, 12.689062527849698],
          tipnames = ["A","B","C","D"])
4×2 DataFrame
 Row │ trait     tipnames 
     │ Float64   String   
─────┼────────────────────
   1 │ 10.392    A
   2 │  9.55741  B
   3 │ 10.177    C
   4 │ 12.6891   D

julia> dfr_hybrid = descendencedataframe(net) # the regressors matching the hybrids (all of them)
4×3 DataFrame
 Row │ shift_6  tipnames  sum     
     │ Float64  String    Float64 
─────┼────────────────────────────
   1 │     0.0  A             0.0
   2 │     0.0  B             0.0
   3 │     0.0  C             0.0
   4 │     1.0  D             1.0

julia> dfr = innerjoin(dat, dfr_hybrid, on=:tipnames); # join data and regressors in a single dataframe

julia> using StatsModels

julia> fitBM = phylolm(@formula(trait ~ shift_6), dfr, net; reml=false) # actual fit
PhyloNetworkLinearModel

Formula: trait ~ 1 + shift_6

Model: Brownian motion

Parameter Estimates, using ML:
phylogenetic variance rate: 0.041206

Coefficients:
────────────────────────────────────────────────────────────────────────
                Coef.  Std. Error      t  Pr(>|t|)  Lower 95%  Upper 95%
────────────────────────────────────────────────────────────────────────
(Intercept)  10.064      0.277959  36.21    0.0008    8.86805   11.26
shift_6       2.72526    0.315456   8.64    0.0131    1.36796    4.08256
────────────────────────────────────────────────────────────────────────
Log Likelihood: -0.7006021946
AIC: 7.4012043891
```

# See also

[`phylolm`](@ref), [`PhyloNetworks.descendencematrix`](@extref).
