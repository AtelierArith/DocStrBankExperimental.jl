```julia
pigeons(pt)

```

Run (a generalization of) Parallel Tempering. 

This will call several rounds of [`run_one_round!()`](@ref),  performing adaptation between each round via [`adapt()`](@ref).

This will also call [`report!()`](@ref), [`write_checkpoint()`](@ref),  and [`run_checks()`](@ref) between rounds. 
