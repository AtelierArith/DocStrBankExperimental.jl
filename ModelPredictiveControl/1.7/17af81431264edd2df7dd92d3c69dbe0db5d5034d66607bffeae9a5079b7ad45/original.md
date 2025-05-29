```
getinfo(mpc::PredictiveController) -> info
```

Get additional info about `mpc` [`PredictiveController`](@ref) optimum for troubleshooting.

The function should be called after calling [`moveinput!`](@ref). It returns the dictionary `info` with the following fields:

!!! info
    Fields with *`emphasis`* are non-Unicode alternatives.


  * `:ΔU` or *`:DeltaU`* : optimal manipulated input increments over $H_c$, $\mathbf{ΔU}$
  * `:ϵ` or *`:epsilon`* : optimal slack variable, $ϵ$
  * `:D̂` or *`:Dhat`* : predicted measured disturbances over $H_p$, $\mathbf{D̂}$
  * `:ŷ` or *`:yhat`* : current estimated output, $\mathbf{ŷ}(k)$
  * `:Ŷ` or *`:Yhat`* : optimal predicted outputs over $H_p$, $\mathbf{Ŷ}$
  * `:Ŷs` or *`:Yhats`* : predicted stochastic output over $H_p$ of [`InternalModel`](@ref), $\mathbf{Ŷ_s}$
  * `:R̂y` or *`:Rhaty`* : predicted output setpoint over $H_p$, $\mathbf{R̂_y}$
  * `:R̂u` or *`:Rhatu`* : predicted manipulated input setpoint over $H_p$, $\mathbf{R̂_u}$
  * `:x̂end` or *`:xhatend`* : optimal terminal states, $\mathbf{x̂}_i(k+H_p)$
  * `:J`   : objective value optimum, $J$
  * `:U`   : optimal manipulated inputs over $H_p$, $\mathbf{U}$
  * `:u`   : current optimal manipulated input, $\mathbf{u}(k)$
  * `:d`   : current measured disturbance, $\mathbf{d}(k)$

For [`LinMPC`](@ref) and [`NonLinMPC`](@ref), the field `:sol` also contains the optimizer solution summary that can be printed. Lastly, the economical cost `:JE` and the custom nonlinear constraints `:gc` values at the optimum are also available for [`NonLinMPC`](@ref).

# Examples

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1, Hc=1);

julia> preparestate!(mpc, [0]); u = moveinput!(mpc, [10]);

julia> round.(getinfo(mpc)[:Ŷ], digits=3)
1-element Vector{Float64}:
 10.0
```
