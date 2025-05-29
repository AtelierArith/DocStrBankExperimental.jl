Solve ODE for Stochastic Death TKTD model

```
$\frac{dx(t)}{dt} = k_d (conc(t) - x(t))$

$\frac{dy(t)}{dt} = k_d (x(t) - z) + h_b$

$ pSurv(t) = \exp{(-y(t))}$
```

**Fields**

  * `tps` – time vector
  * `conc` – exposure vector
  * `kd` – parameters
  * `hb` – background mortality
  * `z` – threshold
  * `kk` – killing rate

Return a Tuple of `Array{Float64,1}`.

# Example

```julia
julia> mySD = runSD([0,1,2,3], [0,1,20,2], 0.5, 2.4, 16.3 ,10.0);

julia> mySD.TK
4-element Array{Float64,1}:
 0.0
 0.21089023114020433
 4.575797874578747
 6.801834882676336

julia> mySD.TD
4-element Array{Float64,1}:
 1.0
 0.09071795328941247
 0.008229747049020037
 0.0007465858083766806
```
