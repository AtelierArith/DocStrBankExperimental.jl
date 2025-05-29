```
VND(;initial, neighborhood, local_search,...)
```

Variable Neighborhood Descent.

# Allowed parameters

  * `initial`: Use this parameter to provide an initial solution (optional).
  * `neighborhood`: Neighborhood structure.
  * `local_search` the local search strategy `BestImproveSearch()` (default) and `FirstImproveSearch()`.

# Example: Knapsack Problem

```julia
import Metaheuristics as MH

struct MyKPNeighborhood <: MH.Neighborhood
    k::Int
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

    # objective function and search space
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)

    # list the neighborhood structures
    neighborhood = [MyKPNeighborhood(1), MyKPNeighborhood(2), MyKPNeighborhood(3)]
    local_search = MH.BestImproveSearch()
    # instantiate VNS
    vnd = MH.VND(;neighborhood, local_search)

    res = MH.optimize(f, search_space, vnd)
    display(res)
end

main()
```
