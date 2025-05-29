```
setmodel!(mpc::PredictiveController, model=mpc.estim.model; <keyword arguments>) -> mpc
```

Set `model` and objective function weights of `mpc` [`PredictiveController`](@ref).

Allows model adaptation of controllers based on [`LinModel`](@ref) at runtime. Modification of [`NonLinModel`](@ref) state-space functions is not supported. New weight matrices in the objective function can be specified with the keyword arguments (see [`LinMPC`](@ref) for the nomenclature). If `Cwt ≠ Inf`, the augmented move suppression weight is $\mathbf{Ñ}_{H_c} = \mathrm{diag}(\mathbf{N}_{H_c}, C)$, else $\mathbf{Ñ}_{H_c} = \mathbf{N}_{H_c}$. The [`StateEstimator`](@ref) `mpc.estim` cannot be a [`Luenberger`](@ref) observer or a [`SteadyKalmanFilter`](@ref) (the default estimator). Construct the `mpc` object with a time-varying [`KalmanFilter`](@ref) instead. Note that the model is constant over the prediction horizon $H_p$.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `mpc::PredictiveController` : controller to set model and weights.
  * `model=mpc.estim.model` : new plant model (not supported by [`NonLinModel`](@ref)).
  * `Mwt=nothing` : new main diagonal in $\mathbf{M}$ weight matrix (vector).
  * `Nwt=nothing` : new main diagonal in $\mathbf{N}$ weight matrix (vector).
  * `Lwt=nothing` : new main diagonal in $\mathbf{L}$ weight matrix (vector).
  * `M_Hp=nothing` : new $\mathbf{M}_{H_p}$ weight matrix.
  * `Ñ_Hc=nothing` or *`Ntilde_Hc`* : new $\mathbf{Ñ}_{H_c}$ weight matrix (see def. above).
  * `L_Hp=nothing` : new $\mathbf{L}_{H_p}$ weight matrix.
  * additional keyword arguments are passed to `setmodel!(mpc.estim)`.

# Examples

```jldoctest
julia> mpc = LinMPC(KalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0)), σR=[√25]), Hp=1, Hc=1);

julia> mpc.estim.model.A[1], mpc.estim.R̂[1], mpc.weights.M_Hp[1], mpc.weights.Ñ_Hc[1]
(0.1, 25.0, 1.0, 0.1)

julia> setmodel!(mpc, LinModel(ss(0.42, 0.5, 1, 0, 4.0)); R̂=[9], M_Hp=[10], Nwt=[0.666]);

julia> mpc.estim.model.A[1], mpc.estim.R̂[1], mpc.weights.M_Hp[1], mpc.weights.Ñ_Hc[1]
(0.42, 9.0, 10.0, 0.666)
```
