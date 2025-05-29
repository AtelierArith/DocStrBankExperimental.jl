```
ExplicitMPC(model::LinModel; <keyword arguments>)
```

Construct an explicit linear predictive controller based on [`LinModel`](@ref) `model`.

The controller minimizes the following objective function at each discrete time $k$:

$$
\begin{aligned}
\min_{\mathbf{ΔU}}   \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}     
                   + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\
                   + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
\end{aligned}
$$

See [`LinMPC`](@ref) for the variable definitions. This controller does not support constraints but the computational costs are extremely low (array division), therefore  suitable for applications that require small sample times. The keyword arguments are identical to [`LinMPC`](@ref), except for `Cwt` and `optim` which are not supported. This controller uses a [`SingleShooting`](@ref) transcription method.

This method uses the default state estimator, a [`SteadyKalmanFilter`](@ref) with default arguments. This controller is allocation-free.

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4);

julia> mpc = ExplicitMPC(model, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
ExplicitMPC controller with a sample time Ts = 4.0 s, SteadyKalmanFilter estimator and:
 30 prediction steps Hp
  1 control steps Hc
  1 manipulated inputs u (0 integrating states)
  4 estimated states x̂
  2 measured outputs ym (2 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```
