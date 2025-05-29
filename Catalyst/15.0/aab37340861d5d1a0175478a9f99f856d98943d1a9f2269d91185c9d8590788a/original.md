```
lat_setp!(sim_struct, p, lrs::LatticeReactionSystem, p_val)
```

For a problem or integrators, update its `p` vector with the input `p_val`. For non-lattice models, this is can be done through direct interfacing (e.g. `prob[p] = 1.0`). However, for `LatticeReactionSystem`-based problems and integrators, this function must be used instead.

Arguments:

  * `sim_struct`: The simulation structure which `u` value we wish to update. Can be either a `ODEProblem`, `JumpProblem`, or an integrator derived from either of these.
  * `p`: The species which value we wish to update. Can be provided either in its symbolic form (e.g. `k`) or as a symbol (e.g. `:k`).
  * `lrs`: The `LatticeReactionSystem` which was used to generate the structure we wish to modify.
  * `p_val`: The parameter's new values. Must be given in a form which is also a valid initial input to the `ODEProblem`/`JumpProblem`.

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
lat_setp!(oprob, :k1, lrs, 0.0) # Sets `k1` to uniformly 0 across the lattice.
lat_setp!(oprob, :k2, lrs, [1.0 0.0 0.0; 0.0 0.0 0.0]) # Sets `k2` to `1.0` in one vertex, and 0 elsewhere.
```
