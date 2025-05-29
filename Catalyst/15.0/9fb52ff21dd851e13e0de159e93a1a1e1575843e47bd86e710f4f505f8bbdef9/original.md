```
lat_getp(sim_struct, p, lrs::LatticeReactionSystem)
```

For a problem or integrators, retrieves its `p` values. For non-lattice models, this is can be done through direct interfacing (e.g. `prob[p]`). However, for `LatticeReactionSystem`-based problems and integrators, this function must be used instead. The output format depends on the lattice (a dense array for cartesian grid lattices, a sparse array for masked grid lattices, and a vector for graph lattices). This format is similar to what is used to designate parameter initial values.

Arguments:

  * `sim_struct`: The simulation structure which `p` value we wish to retrieve. Can be either a `ODEProblem`,

`JumpProblem`, or an integrator derived from either of these.

  * `p`: The species which value we wish to update. Can be provided either in its symbolic form (e.g. `k`) or as a symbol (e.g. `:k`).
  * `lrs`: The `LatticeReactionSystem` which was used to generate the structure we wish to modify.

Notes:

  * Even if the parameter is spatially uniform, a full array with its values across all vertices will be retrieved.

Example:

```julia
# Prepare `LatticeReactionSystem`s.
using Catalyst
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
lrs = LatticeReactionSystem(rs, [tr], CartesianGrid((2,3)))

# Prepares a corresponding ODEProblem.
u0 = [:X1 => 1.0, :X2 => 2.0]
tspan = (0.0, 50.0)
ps = [:k1 => [1.0 2.0 3.0; 4.0 5.0 6.0], :k2 => 1.0, :D => 0.01]
oprob = ODEProblem(lrs, u0, tspan, ps)

# Updates the `ODEProblem`.
lat_getp(oprob, :k1, lrs) # Retrieves the value of `k1`.
```
