```
lancichinetti_fortunato_radicchi(n::Integer, k_avg::Integer, k_max::Integer)
```

Create a [Lancichinetti-Fortunato-Radicchi model](https://en.wikipedia.org/wiki/Lancichinetti-Fortunato-Radicchi_benchmark) random graph with `n` vertices, `k_avg` average degree, and `k_max` maximum degree. The model generates graphs with a power-law degree distribution and community structure. Abstractly, we can think of it as an SBM with power-law distribution for the community size and the degree distribution.

### Optional Arguments

  * `mixing_parameter`: mixing parameter μ, defines the average average ratio of {external degree}/{total degree}
  * `is_directed=false`: if true, return a directed graph.
  * `seed=1`: set the random seed.
  * `tau=2.0`: exponent for the power-law degree distribution for degree distribution.
  * `tau2=1.0`: exponent for the power-law degree distribution for community size distribution.
  * `nmin=nothing`, `nmax=nothing`: minimum and maximum (range) for community sizes.
  * `overlapping_nodes=0`: number of overlapping nodes.
  * `overlap_membership=0`: number of memberships for overlapping nodes.
  * `clustering_coeff=nothing`: if specified,  the program will perform a number of rewiring to increase the average cluster coefficient up to the wished value.

### Other options

If you want to produce a benchmark whose distribution of the ratio of external degree/total degree is superiorly (inferiorly) bounded by the mixing parameter. In other words, if you use one of these options, the mixing parameter is not the average ratio of external degree/total degree (as it used to be) but the maximum (or the minimum) of that distribution. When using one of these options, what the program essentially does is to approximate the external degree always by excess (or by defect) and if necessary to modify the degree distribution. Nevertheless, this last possibility occurs for a few nodes and numerical simulations show that it does not affect the degree distribution appreciably.

  * `excess=false`: if true, the degree distribution is superiorly bounded by μ.
  * `defect=false`: if true, the degree distribution is inferiorly bounded by μ.

!!! warning "Use of excess and defect options"
    Both options `excess` and `defect` cannot be `true` at the same time


### Notes

Depending on the input parameter combination, the function may not converge to a solution. If this happens, try different input parameters.

### References

  * Benchmarks for testing community detection algorithms on directed and weighted graphs with overlapping communities, Andrea Lancichinetti and Santo Fortunato, 2009. [https://doi.org/10.1103/PhysRevE.80.016118](https://doi.org/10.1103/PhysRevE.80.016118)
  * Benchmark graphs for testing community detection algorithms, Andrea Lancichinetti, Santo Fortunato, and Filippo Radicchi, 2008. [https://doi.org/10.1103/PhysRevE.78.046110](https://doi.org/10.1103/PhysRevE.78.046110)
  * Link to [the original source code by the authors](https://sites.google.com/site/andrealancichinetti/benchmarks?authuser=0)

## Examples

```jldoctest
julia> using LFRBenchmarkGraphs

julia> g,cid = lancichinetti_fortunato_radicchi(20, 4, 5);

julia> g
{20, 35} undirected simple Int64 graph

julia> println(cid)  # community labels
[1, 1, 3, 2, 3, 2, 1, 2, 1, 1, 1, 3, 1, 3, 2, 3, 3, 1, 2, 3]

```
