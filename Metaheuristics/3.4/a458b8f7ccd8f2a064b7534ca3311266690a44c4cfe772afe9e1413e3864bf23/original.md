```
VNS(;initial, neighborhood_shaking, neighborhood_local, local_search, neighborhood_change)
```

General Variational Neighborhood Search.

# Allowed parameters

  * `initial`: Use this parameter to provide an initial solution (optional).
  * `neighborhood_shaking`: Neighborhood structure for the shaking step.
  * `neighborhood_local`: Neighborhood structure for the local search.
  * `local_search`: the local search strategy `BestImproveSearch()` (default) and `FirstImproveSearch()`.
  * `neighborhood_change`: The procedure for changing among neighborhood structures  (default `SequentialChange()`).

# Example: Knapsack Problem

```julia
import Metaheuristics as MH

struct MyKPNeighborhood <: MH.Neighborhood
    k::Int
end

function MH.neighborhood_structure(x, s::MyKPNeighborhood, rng)
    # this is defined due to shaking procedure requires a random one
    # not the i-th neighbor.
    i = rand(rng, 1:length(x))
    reverse!(view(x, i:min(length(x), i+s.k)))
    x
end

function MH.neighborhood_structure(x, s::MyKPNeighborhood, i::Integer)
    # return the i-th neighbor around x, regarding s.k structure
    i > length(x) && return nothing
    reverse!(view(x, i:min(length(x), i+s.k)))
    x
end

function main()
    profit = [55, 10,47, 5, 4, 50, 8, 61, 85, 87]
    weight = [95, 4, 60, 32, 23, 72, 80, 62, 65, 46]
    capacity = 269
    nitems = length(weight)

    # objective function and search space
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)

    # list the neighborhood structures
    neighborhood_shaking = [MyKPNeighborhood(6), MyKPNeighborhood(5), MyKPNeighborhood(4)]
    neighborhood_local = [MyKPNeighborhood(3), MyKPNeighborhood(2), MyKPNeighborhood(1)]
    local_search = MH.BestImproveSearch()
    # instantiate VNS
    vnd = MH.VNS(;neighborhood_shaking, neighborhood_local, local_search, options=MH.Options(verbose=true))

    res = MH.optimize(f, search_space, vnd)
    display(res)
end

main()
```
