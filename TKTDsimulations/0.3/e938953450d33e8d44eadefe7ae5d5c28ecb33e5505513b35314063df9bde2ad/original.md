```
Solve Toxicokinetics Models with a single parameter

$\frac{dx(t)}{dt} = k_d (conc(t) - x(t))$
```

**Fields**     - `tps` – time vector     - `conc` – exposure vector     - `kd` – parameter, a scalar

Return a Tuple with `Array{Float64,1}` of th same length as `tps`

# Example

```julia
julia> myTK = runTK([0,1,2,3], [0,1,20,2], 0.5);
julia> myTK.TK
4-element Array{Float64,1}:
 0.0
 0.21800446293645104
 4.570824232907027
 6.801199145490319
```
