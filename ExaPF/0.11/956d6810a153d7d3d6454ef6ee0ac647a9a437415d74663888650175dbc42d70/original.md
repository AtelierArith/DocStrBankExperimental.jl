```
run_pf(
    polar::PolarForm, stack::NetworkStack;
    rtol=1e-8, max_iter=20, verbose=0,
)
```

Solve the power flow equations $g(x, u) = 0$ w.r.t. the stack $x$, using the ([`NewtonRaphson`](@ref) algorithm. The initial state $x$ is specified implicitly inside `stack`, with the mapping [`mapping`](@ref) associated to the polar formulation. The object `stack` is modified inplace in the function.

The algorithm stops when a tolerance `rtol` or a maximum number of iterations `maxiter` is reached.

### Arguments

  * `polar::AbstractFormulation`: formulation of the power flow equation
  * `stack::NetworkStack`: initial values in the network

### Examples

```jldoctest; setup=:(using ExaPF)
julia> polar = ExaPF.load_polar("case9");

julia> stack = ExaPF.NetworkStack(polar);

julia> conv = run_pf(polar, stack);

julia> conv.has_converged
true

julia> conv.n_iterations
4
```
