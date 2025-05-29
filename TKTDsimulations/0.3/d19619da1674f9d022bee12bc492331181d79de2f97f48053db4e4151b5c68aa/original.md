Solve ODE for Individual Tolerance TKTD model

```
$\frac{dx(t)}{dt} = k_d (conc(t) - x(t))$

$ pSurv(t) = \exp{(-h_b t)} (1-logLogistic(max(x(t), alpha,beta))  $
```

**Fields**

  * `tps` – time vector
  * `conc` – exposure vector
  * `kd` – toxicokinetics parameter
  * `hb` – background mortality
  * `alpha` – median of log-logistic distribution
  * `beta` – shape of the log-logistic distribution

Return an `Array{Float64,1}`.

# Example

```julia
julia> myIT = runIT([0,1,2,3], [0,1,20,2], 0.5, 2.1, 10.5 , 2.4);

julia> myIT.TK
4-element Array{Float64,1}:
 0.0
 0.21800446293645104
 4.570824232907027
 6.801199145490319
 
julia> myIT.TD
4-element Array{Float64,1}:
 1.0
 0.12244522344410577
 0.013201809910381767
 0.001357555235565695
```
