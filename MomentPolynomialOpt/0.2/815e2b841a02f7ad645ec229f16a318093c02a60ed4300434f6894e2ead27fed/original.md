```julia
v, M = optimize(M, optimizer)
```

Run the optimizer on the moment program `M` using the optimizer `optimizer` and output the objective_value `v` and the moment program `M`. If the optimization program has no solution, it returns `nothing` and `M`. 
