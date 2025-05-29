```
LinMPC(estim::StateEstimator; <keyword arguments>)
```

Use custom state estimator `estim` to construct `LinMPC`.

`estim.model` must be a [`LinModel`](@ref). Else, a [`NonLinMPC`](@ref) is required. 

# Examples

```jldoctest
julia> estim = KalmanFilter(LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4), i_ym=[2]);

julia> mpc = LinMPC(estim, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
LinMPC controller with a sample time Ts = 4.0 s, OSQP optimizer, KalmanFilter estimator and:
 30 prediction steps Hp
  1 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  3 estimated states x̂
  1 measured outputs ym (1 integrating states)
  1 unmeasured outputs yu
  0 measured disturbances d
```
