```
initstate!(estim::StateEstimator, u, ym, d=[]) -> x̂
```

Init `estim.x̂0` states from current inputs `u`, measured outputs `ym` and disturbances `d`.

The method tries to find a good steady-state for the initial estimate $\mathbf{x̂}$. It removes the operating points with [`remove_op!`](@ref) and call [`init_estimate!`](@ref):

  * If `estim.model` is a [`LinModel`](@ref), it finds the steady-state of the augmented model using `u` and `d` arguments, and uses the `ym` argument to enforce that  $\mathbf{ŷ^m}(0) = \mathbf{y^m}(0)$. For control applications, this solution produces a bumpless manual to automatic transfer. See [`init_estimate!`](@ref) for details.
  * Else, `estim.x̂0` is left unchanged. Use [`setstate!`](@ref) to manually modify it.

If applicable, it also sets the error covariance `estim.P̂` to `estim.P̂_0`.

# Examples

```jldoctest
julia> estim = SteadyKalmanFilter(LinModel(tf(3, [10, 1]), 0.5), nint_ym=[2], direct=false);

julia> u = [1]; y = [3 - 0.1]; x̂ = round.(initstate!(estim, u, y), digits=3)
3-element Vector{Float64}:
 10.0
  0.0
 -0.1

julia> x̂ ≈ updatestate!(estim, u, y)
true

julia> evaloutput(estim) ≈ y
true
```
