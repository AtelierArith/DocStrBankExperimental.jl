```
getinfo(estim::MovingHorizonEstimator) -> info
```

Get additional info on `estim` [`MovingHorizonEstimator`](@ref) optimum for troubleshooting.

If `estim.direct==true`, the function should be called after calling [`preparestate!`](@ref). Otherwise, call it after [`updatestate!`](@ref). It returns the dictionary `info` with the following fields:

!!! info
    Fields with *`emphasis`* are non-Unicode alternatives.


  * `:Ŵ` or *`:What`* : optimal estimated process noise over $N_k$, $\mathbf{Ŵ}$
  * `:ϵ` or *`:epsilon`* : optimal slack variable, $ϵ$
  * `:X̂` or *`:Xhat`* : optimal estimated states over $N_k+1$, $\mathbf{X̂}$
  * `:x̂` or *`:xhat`* : optimal estimated state, $\mathbf{x̂}_k(k+p)$
  * `:V̂` or *`:Vhat`* : optimal estimated sensor noise over $N_k$, $\mathbf{V̂}$
  * `:P̄` or *`:Pbar`* : estimation error covariance at arrival, $\mathbf{P̄}$
  * `:x̄` or *`:xbar`* : optimal estimation error at arrival, $\mathbf{x̄}$
  * `:Ŷ` or *`:Yhat`* : optimal estimated outputs over $N_k$, $\mathbf{Ŷ}$
  * `:Ŷm` or *`:Yhatm`* : optimal estimated measured outputs over $N_k$, $\mathbf{Ŷ^m}$
  * `:x̂arr` or *`:xhatarr`* : optimal estimated state at arrival, $\mathbf{x̂}_k(k-N_k+p)$
  * `:J`   : objective value optimum, $J$
  * `:Ym`  : measured outputs over $N_k$, $\mathbf{Y^m}$
  * `:U`   : manipulated inputs over $N_k$, $\mathbf{U}$
  * `:D`   : measured disturbances over $N_k$, $\mathbf{D}$
  * `:sol` : solution summary of the optimizer for printing

# Examples

```jldoctest
julia> model = LinModel(ss(1.0, 1.0, 1.0, 0, 5.0));

julia> estim = MovingHorizonEstimator(model, He=1, nint_ym=0, direct=false);

julia> updatestate!(estim, [0], [1]);

julia> round.(getinfo(estim)[:Ŷ], digits=3)
1-element Vector{Float64}:
 0.5
```
