```
estimate_x0(sys, d, n = min(length(d), 3 * slowest_time_constant(sys)); fixed = fill(NaN, sys.nx)
```

Estimate the initial state of the system 

# Arguments:

  * `d`: [`iddata`](@ref)
  * `n`: Number of samples to use.
  * `fixed`: If a vector of the same length as `x0` is provided, finite values indicate fixed values that are not to be estimated, while nonfinite values are free.

# Example

```julia
sys   = ssrand(2,3,4, Ts=1)
x0    = randn(sys.nx)
u     = randn(sys.nu, 100)
y,t,x = lsim(sys, u; x0)
d     = iddata(y, u, 1)
x0h   = estimate_x0(sys, d, 8, fixed=[Inf, x0[2], Inf, Inf])
x0h[2] == x0[2] # Should be exact equality
norm(x0-x0h)    # Should be small
```
