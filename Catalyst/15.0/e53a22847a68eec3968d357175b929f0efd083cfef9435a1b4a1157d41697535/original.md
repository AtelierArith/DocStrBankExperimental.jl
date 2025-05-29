```
lat_getu(sol, sp, lrs::LatticeReactionSystem; t = nothing)
```

A function for retrieving the solution of a `LatticeReactionSystem`-based simulation on various desired forms. Generally, for `LatticeReactionSystem`s, the values in `sol` is ordered in a way which is not directly interpretable by the user. Furthermore, the normal Catalyst interface for solutions (e.g. `sol[:X]`) does not work for these solutions. Hence this function is used instead.

The output is a vector, which in each position contains sp's value (either at a time step of time, depending on the input `t`). Its shape depends on the lattice (using a similar form as heterogeneous initial conditions). I.e. for a NxM cartesian grid, the values are NxM matrices. For a masked grid, the values are sparse matrices. For a graph lattice, the values are vectors (where the value in the n'th position corresponds to sp's value in the n'th vertex).

Arguments:

  * `sol`: The solution from which we wish to retrieve some values.
  * `sp`: The species which value we wish to update. Can be provided either in its symbolic form (e.g. `X`) or as a symbol (e.g. `:X`).
  * `lrs`: The `LatticeReactionSystem` which was simulated to generate the solution.
  * `t = nothing`: If `nothing`, we simply return the solution across all saved time steps (default). If `t` instead is a vector (or range of values), returns the solution interpolated at these time points.

Notes:

  * The `lat_getu` is not optimised for performance. However, it should still be quite performant, but there might be some limitations if called a very large number of times.
  * Long-term it is likely that this function gets replaced with a sleeker interface.

Example:

```julia
using Catalyst, OrdinaryDiffEqDefault

# Prepare `LatticeReactionSystem`s.
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
lrs = LatticeReactionSystem(rs, [tr], CartesianGrid((2,2)))

# Create problems.
u0 = [:X1 => 1, :X2 => 2]
tspan = (0.0, 10.0)
ps = [:k1 => 1, :k2 => 2.0, :D => 0.1]

oprob = ODEProblem(lrs1, u0, tspan, ps)
osol = solve(oprob)
lat_getu(osol, :X1, lrs) # Returns the value of X1 at each time step.
lat_getu(osol, :X1, lrs; t = 0.0:10.0) # Returns the value of X1 at times 0.0, 1.0, ..., 10.0
```
