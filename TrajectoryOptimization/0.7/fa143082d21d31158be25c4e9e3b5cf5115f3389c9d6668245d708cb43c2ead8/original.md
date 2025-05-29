```
Objective{C}
```

Objective: stores stage cost(s) and terminal cost functions. All the cost functions at each time step must have the same type.

Constructors:

```
Objective(cost, N)
Objective(cost, cost_term, N)
Objective(costs::Vector{<:CostFunction}, cost_term)
Objective(costs::Vector{<:CostFunction})
```
