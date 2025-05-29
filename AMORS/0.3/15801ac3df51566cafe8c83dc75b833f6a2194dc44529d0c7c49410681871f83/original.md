```
AMORS.solve!(f, x, y) -> info, x, y
```

Estimate the components of a *bilinear model* by the AMORS method. The argument `f` represents the objective function (see below). On entry, arguments `x` and `y` are the initial variables of the problem, they are overwritten by the solution (call [`AMORS.solve`](@ref) for an out-of-place version of the algorithm). The result is a 3-tuple with the updated variables and `info` storing the final state of the algorithm. For example, `info.status == :convergence` holds if algorithm has converged in the variables `x` and `y` within the given tolerances or `info.status == :too_many_iterations` holds if the algorithm exceeded the maximum number of iterations (see [`AMORS.Info`](@ref) for more details).

The objective of AMORS is to minimize in `x ∈ 𝕏` and `y ∈ 𝕐` an objective function of the form:

```
F(x,y,μ,ν) = G(x⊗y) + μ*J(x) + ν*K(y)
```

where `G` is a function of the *bilinear model* `x⊗y`, `J` and `K` are nonnegative homogeneous functions of the respective variables `x` and `y`, `μ > 0` and `ν > 0` are hyper-parameters. The notation `x⊗y` denotes a *bilinear model* which has the following invariance property:

```
(α*x)⊗(y/α) = x⊗y
```

for any `x`, `y`, and scalar factor `α > 0`. An *homogeneous function*, say `J: 𝕏 → ℝ`, of degree `q` is such that `J(α*x) = abs(α)^q*J(x)` for any `α ∈ ℝ` and for any `x ∈ 𝕏` with `𝕏` the domain of `J`. It can be noted that the following property must hold `∀ α ∈ ℝ`: `x ∈ 𝕏` implies that `α*x ∈ 𝕏`. In other words, `𝕏` must be a cone.

The argument `f` is a callable object that collects any data, workspaces, parameters, etc. needed to compute the objective function `F(x,y,μ,ν)`. The argument `f` is called as `f(Val(task), args...)` where `task` is a symbolic name specifying the operation to be performed:

```
f(Val(:degJ))       -> deg(J)  # unless keyword `q` is specified
f(Val(:degK))       -> deg(K)  # unless keyword `r` is specified
f(Val(:Jx), x)      -> J(x)
f(Val(:Ky), y)      -> K(y)
f(Val(:x), x, y, μ) -> x⁺, G(x⁺⊗y), J(x⁺)
f(Val(:y), x, y, ν) -> y⁺, G(x⊗y⁺), K(y⁺)
```

where `deg(J)` and `deg(K)` denote the respective homogeneous degrees of the functions `J` and `K` and with:

```
x⁺ ≈ argmin_{x ∈ 𝕏} G(x⊗y) + μ*J(x)
y⁺ ≈ argmin_{y ∈ 𝕐} G(x⊗y) + ν*K(y)
```

The solution of `argmin_{x ∈ 𝕏} F(x, y)` and `argmin_{y ∈ 𝕐} F(x, y)` may not be exact and may be computed in-place to save storage, that is `x` (resp. `y`) being overwritten by the solution `x⁺` (resp. `y⁺`). For type stability of the algorithm, `f(Val(:x),x,y,μ)[1]::typeof(x)` and `f(Val(:y),x,y,ν)[1]::typeof(y)` must hold.

Arguments `x` and `y` are needed to define the variables of the problem. Initially, they must be such that `J(x) > 0` and `K(y) > 0` unless automatic best rescaling is disabled by `autoscale=false` (which is not recommended).

The following keywords can be specified:

  * `μ` is the multiplier of `J(x)`; `μ = 1.0` by default.
  * `ν` is the multiplier of `K(y)`; `ν = 1.0` by default.
  * `q` is the homogeneous degree of `J(x)`; `q = f(Val(:degJ))` by default.
  * `r` is the homogeneous degree of `K(y)`; `r = f(Val(:degK))` by default.
  * `α` is the initial scaling factor; `α = 1.0` by default. If `autoscale` is `false`, the value of `α` is unchanged for all iterations.
  * `autoscale` specifies whether to automatically set the scaling factor `α`; `autoscale = true` by default. This keyword is provided for testing the efficiency of the AMORS algorithm, it is recommended to not disable autoscaling.
  * `Float` is the floating-point type for scalar computations; `Float = Float64` by default.
  * `first` is one of `Val(:x)` or `Val(:y)` (the default) to specify which component to update the first given the other.
  * `αtol ≥ 0` is a relative tolerance (`αtol = 0.3` by default) to assert the convergence in the scaling factor `α` in the intial iteration of the algorithm. Use `αtol = Inf` to simply update `α` without checking for convergence. The value of `αtol` has no effects if `autoscale` is `false`.
  * `xtol ≥ 0` is a relative tolerance (`xtol = 0.0001` by default) to assert the convergence in the variables `x`.
  * `ytol ≥ 0` is a relative tolerance (`ytol = xtol` by default) to assert the convergence in the variables `y`.
  * `maxiter` is the maximum number of algorithm iterations (`1000` by default). An iteration of the algorithm consists in updating one of the component of the bilinear model, `x` or `y`. Two iterations are therefore needed to completely update the model.
  * `has_converged` is a function used to check for convergence of the iterates ([`AMORS.has_converged`](@ref) by default).
  * `observer` is a user-defined function called after ever iteration as `observer(io,info,f,x,y)` with `io` the stream set by the corresponding keyword, `info` an instance of [`AMORS.Info`](@ref) with the current state of the algorithm, `f` the object defining the problem, and `x` and `y` the current estimates of the model components. This function may return a symbolic status, if this status is not `:searching`, then the algorithm will be terminated and the resulting `info` will be set with this status. The value returned by the observer is ignored if it is not a `Symbol`.
  * `io` the stream for the observer, `stdout` by default.
