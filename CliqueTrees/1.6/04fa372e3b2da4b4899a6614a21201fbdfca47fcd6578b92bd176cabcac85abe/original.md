```
METIS <: EliminationAlgorithm

METIS(; ctype=-1, rtype=-1, nseps=-1, niter=-1, seed=-1,
        compress=-1, ccorder=-1, pfactor=-1, ufactor=-1)
```

The multilevel [nested dissection](https://en.wikipedia.org/wiki/Nested_dissection) algorithm implemented in METIS.

```julia-repl
julia> using CliqueTrees, Metis

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> alg = METIS(ctype=Metis.METIS_CTYPE_RM)
METIS:
    ctype: 0
    rtype: -1
    nseps: -1
    niter: -1
    seed: -1
    compress: -1
    ccorder: -1
    pfactor: -1
    ufactor: -1


julia> treewidth(graph; alg)
3
```

### Parameters

  * `ctype`: matching scheme to be used during coarsening
  * `rtype`: algorithm used for refinement
  * `nseps`: number of different separators computed at each level of nested dissection
  * `niter`: number of iterations for refinement algorithm at each stage of the uncoarsening process
  * `seed`: random seed
  * `compress`: whether to combine vertices with identical adjacency lists
  * `ccorder`: whether to order connected components separately
  * `pfactor`: minimum degree of vertices that will be ordered last
  * `ufactor`: maximum allowed load imbalance partitions

### References

  * Karypis, George, and Vipin Kumar. "A fast and high quality multilevel scheme for partitioning irregular graphs." *SIAM Journal on Scientific Computing* 20.1 (1998): 359-392.
