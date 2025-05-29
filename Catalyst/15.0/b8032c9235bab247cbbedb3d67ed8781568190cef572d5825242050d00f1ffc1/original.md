```
steady_state_jac(rs::ReactionSystem; u0 = [])
```

Creates the Jacobian function which can be used as input to `steady_state_stability`. Useful when  a large number of stability computation has to be carried out in a performant manner.

Arguments:     - `rs`: The reaction system model for which we want to compute stability.     - `u0 = []`: For systems with conservation laws, a `u` is required to compute the conserved quantities.

Example:

```julia
# Creates model.
rn = @reaction_network begin
    (p,d), 0 <--> X
end
p = [:p => 1.0, :d => 0.5]

# Creates the steady state jacobian.
ss_jac = steady_state_jacobian(rn)

# Finds (the trivial) steady state, and computes stability.
steady_state = [2.0]
steady_state_stability(steady_state, rn, p; ss_jac)

Notes:
    - In practise, this function returns an `ODEProblem` (with a computed Jacobian) set up in 
    such a way that it can be used by the `steady_state_stability` function.
```
