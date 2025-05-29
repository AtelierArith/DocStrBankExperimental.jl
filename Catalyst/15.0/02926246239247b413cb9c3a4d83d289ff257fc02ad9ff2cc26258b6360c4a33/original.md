```
rebuild_lat_internals!(sciml_struct)
```

Rebuilds the internal functions for simulating a LatticeReactionSystem. Whenever a problem or integrator has had its parameter values updated, this function should be called for the update to be taken into account. For ODE simulations, `rebuild_lat_internals!` needs only to be called when

  * An edge parameter has been updated.
  * When a parameter with spatially homogeneous values has been given spatially heterogeneous values (or vice versa).

Arguments:

  * `sciml_struct`: The problem (e.g. an `ODEProblem`) or an integrator which we wish to rebuild.

Notes:

  * Currently does not work for `DiscreteProblem`s, `JumpProblem`s, or their integrators.
  * The function is not built with performance in mind, so avoid calling it multiple times in performance-critical applications.

Example:

```julia
# Creates an initial `ODEProblem`
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
grid = CartesianGrid((2,2))
lrs = LatticeReactionSystem(rs, [tr], grid)

u0 = [:X1 => 2, :X2 => [5 6; 7 8]]
tspan = (0.0, 10.0)
ps = [:k1 => 1.5, :k2 => [1.0 1.5; 2.0 3.5], :D => 0.1]

oprob = ODEProblem(lrs, u0, tspan, ps)

# Updates parameter values.
oprob.ps[:ks] = [2.0 2.5; 3.0 4.5]
oprob.ps[:D] = 0.05

# Rebuilds `ODEProblem` to make changes have an effect.
rebuild_lat_internals!(oprob)
```
