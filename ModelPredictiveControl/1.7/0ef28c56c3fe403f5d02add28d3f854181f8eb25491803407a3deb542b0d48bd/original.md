```
moveinput!(mpc::PredictiveController, ry=mpc.estim.model.yop, d=[]; <keyword args>) -> u
```

Compute the optimal manipulated input value `u` for the current control period.

Solve the optimization problem of `mpc` [`PredictiveController`](@ref) and return the results $\mathbf{u}(k)$. Following the receding horizon principle, the algorithm discards the optimal future manipulated inputs $\mathbf{u}(k+1), \mathbf{u}(k+2), ...$ Note that the method mutates `mpc` internal data (it stores `u - mpc.estim.model.uop` at `mpc.lastu0` for instance) but it does not modifies `mpc.estim` states. Call [`preparestate!(mpc, ym, d)`](@ref) before `moveinput!`, and [`updatestate!(mpc, u, ym, d)`](@ref) after, to update `mpc` state estimates. Setpoint and measured disturbance previews can be implemented with the `R̂y`, `R̂u` and `D̂` keyword arguments. 

Calling a [`PredictiveController`](@ref) object calls this method.

See also [`LinMPC`](@ref), [`ExplicitMPC`](@ref), [`NonLinMPC`](@ref).

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `mpc::PredictiveController` : solve optimization problem of `mpc`.
  * `ry=mpc.estim.model.yop` : current output setpoints $\mathbf{r_y}(k)$.
  * `d=[]` : current measured disturbances $\mathbf{d}(k)$.
  * `D̂=repeat(d, mpc.Hp)` or *`Dhat`* : predicted measured disturbances $\mathbf{D̂}$, constant  in the future by default or $\mathbf{d̂}(k+j)=\mathbf{d}(k)$ for $j=1$ to $H_p$.
  * `R̂y=repeat(ry, mpc.Hp)` or *`Rhaty`* : predicted output setpoints $\mathbf{R̂_y}$, constant  in the future by default or $\mathbf{r̂_y}(k+j)=\mathbf{r_y}(k)$ for $j=1$ to $H_p$.
  * `R̂u=mpc.Uop` or *`Rhatu`* : predicted manipulated input setpoints $\mathbf{R̂_u}$, constant  in the future by default or $\mathbf{r̂_u}(k+j)=\mathbf{u_{op}}$ for $j=0$ to $H_p-1$.

# Examples

```jldoctest
julia> mpc = LinMPC(LinModel(tf(5, [2, 1]), 3), Nwt=[0], Hp=1000, Hc=1);

julia> preparestate!(mpc, [0]); ry = [5];

julia> u = moveinput!(mpc, ry); round.(u, digits=3)
1-element Vector{Float64}:
 1.0
```
