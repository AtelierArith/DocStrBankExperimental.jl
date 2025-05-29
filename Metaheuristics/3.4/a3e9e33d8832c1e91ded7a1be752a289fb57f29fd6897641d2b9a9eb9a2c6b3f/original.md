```
GRASP(;initial, constructor, local_search,...)
```

Greedy Randomized Adaptive Search Procedure.

# Allowed parameters

  * `initial`: an initial solution if necessary.
  * `constructor` parameters for the greedy constructor.
  * `local_search` the local search strategy `BestImproveSearch()` (default) and `FirstImproveSearch()`.

See [`GreedyRandomizedConstructor`](@ref)

# Example: Knapsack Problem

```julia
import Metaheuristics as MH

# define type for saving knapsack problem instance
struct KPInstance
    profit
    weight
    capacity
end

function MH.compute_cost(candidates, constructor, instance::KPInstance)
    # Ration profit / weight
    ratio = instance.profit[candidates] ./ instance.weight[candidates]
    # It is assumed minimizing non-negative costs
    maximum(ratio) .- ratio
end

function main()
    # problem instance
    profit = [55, 10,47, 5, 4, 50, 8, 61, 85, 87]
    weight = [95, 4, 60, 32, 23, 72, 80, 62, 65, 46]
    capacity = 269
    optimum = 295
    instance = KPInstance(profit, weight, capacity)

    # objective function and search space
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)
    candidates = rand(search_space)

    # define each GRASP component
    constructor  = MH.GreedyRandomizedConstructor(;candidates, instance, α = 0.95)
    local_search = MH.BestImproveSearch()
    neighborhood = MH.TwoOptNeighborhood()
    grasp = MH.GRASP(;constructor, local_search)
    
    # optimize and display results
    result = MH.optimize(f, search_space, grasp)
    display(result)
    # compute GAP
    fx = -minimum(result)
    GAP = (optimum - fx) / optimum
    println("The GAP is ", GAP)
end

main()
```
