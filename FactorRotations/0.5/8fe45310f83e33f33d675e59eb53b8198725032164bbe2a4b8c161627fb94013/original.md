```
reflect!(r::FactorRotation)
```

Modify `r` in-place by swapping signs of the loading matrix `r.L` such that the sum of each column is positive. The rotation matrix `r.T` and factor correlation matrix `r.phi` are updated accordingly.

## Examples

```jldoctest
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];


julia> r = rotate(L, Varimax());

julia> r_reflected = reflect!(r)
FactorRotation{Float64} with loading matrix:
8×2 Matrix{Float64}:
 0.886061  0.246196
 0.924934  0.183253
 0.894664  0.155581
 0.865205  0.221416
 0.264636  0.893176
 0.206218  0.786653
 0.156572  0.724884
 0.269424  0.67595

julia> r == r_reflected
true
```
