```
stability(u::Vector{T}, rs::ReactionSystem, p; tol = 10*sqrt(eps())
            ss_jac = steady_state_jac(u, rs, p))
```

Compute the stability of a steady state (Returned as a `Bool`, with `true` indicating stability).

Arguments:

  * `u`: The steady state for which we want to compute stability.
  * `rs`: The `ReactionSystem` model for which we want to compute stability.
  * `p`: The parameter set for which we want to compute stability.
  * `tol = 10*sqrt(eps())`: The tolerance used for determining whether computed eigenvalues real

parts can reliably be considered negative/positive. In practise, a steady state is considered  stable if the corresponding Jacobian's maximum eigenvalue real part is < 0. However, if this maximum  eigenvalue is in the range `-tol< eig < tol`, and error is throw, as we do not deem that stability can be ensured with enough certainty. The choice `tol = 10*sqrt(eps())` has *not* been subject to much analysis.

  * `ss_jac = steady_state_jac(u, rs)`: It is possible to pre-compute the

Jacobian used for stability computation using `steady_state_jac`. If stability is computed  for many states, precomputing the Jacobian may speed up evaluation.

Example:

```julia
# Creates model.
rn = @reaction_network begin
    (p,d), 0 <--> X
end
p = [:p => 1.0, :d => 0.5]

# Finds (the trivial) steady state, and computes its stability.
steady_state = [2.0]
steady_state_stability(steady_state, rn, p)

Notes:
- The input `u` can (currently) be both a vector of values (like `[1.0, 2.0]`) and a vector map 
(like `[X => 1.0, Y => 2.0]`). The reason is that most methods for computing stability only
produces vectors of values. However, if possible, it is recommended to work with values on the
form of maps.
- Catalyst currently computes steady state stabilities using the naive approach of checking whether
a system's largest eigenvalue real part is negative. While more advanced stability computation 
methods exist (and would be a welcome addition to Catalyst), there is no direct plans to implement 
these. Furthermore, Catalyst uses a tolerance `tol = 10*sqrt(eps())` to determine whether a 
computed eigenvalue is far away enough from 0 to be reliably used. This selected threshold can be changed through the `tol` argument.
```
