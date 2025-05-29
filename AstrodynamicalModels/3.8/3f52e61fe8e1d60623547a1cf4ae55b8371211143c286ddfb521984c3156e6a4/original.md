```julia
NBFunction(N; stm, name, kwargs...)

```

Returns an `ODEFunction` for NBP dynamics. The order of states and parameters in the `ODEFunction` arguments are equivalent to the order of states and parameters for the system produced with `NBP(N)`. As a general rule, the order of the states follows: `[x₁, y₁, z₁, ..., xₙ, yₙ, zₙ, ẋ₁, ẏ₁, ż₁, ..., ẋₙ, ẏₙ, żₙ]`.

!!! note
    Unlike `R2BP` and `CR3BP`, `jac` is set to `false` by default. The number of states for `NBP` systems can be very large for relatively small numbers of bodies (`N`). Enabling `jac=true` by default would cause unnecessarily long waiting times for this @memoize function to return for `N ≥ 3` or so. If `N=2` and `stm=true`, setting `jac=true` could still result in several minutes of calculations, depending on the computer you're using.


!!! warning
    Be careful about specifying `stm=true` for systems with `N ≥ 3`! If state transition matrix dynamics are enabled, you can calculate the total number of system states with `N*6 + (N*6)^2`. Note that this increases exponentially as `N` grows! For `N == 6`, unless you're using parallelization, your computer may run for several hours.


# Extended Help

### Usage

The `stm`, and `name` keyword arguments are passed to `NBP`. All other keyword arguments are passed directly to `SciMLBase.ODEFunction`.

```julia
f = NBFunction(3; stm=false, name=:NBP, jac=false, sparse=false)
let u = randn(3*6), p = randn(1 + 3), t = 0
    f(u, p, t)
end
```
