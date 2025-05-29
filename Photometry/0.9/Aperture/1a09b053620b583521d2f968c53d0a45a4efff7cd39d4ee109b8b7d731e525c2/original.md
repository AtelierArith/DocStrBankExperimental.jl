```
CircularAperture(x, y, r)
CircularAperture(position, r)
```

A circular aperture.

A circular aperture with radius `r`. `r` must be greater than or equal to 0.

# Examples

```jldoctest
julia> ap = CircularAperture(0, 0, 10)
21×21 CircularAperture{Int64} with indices -10:10×-10:10:
 0          0         0           …  0           0         0
 0          0         0              0           0         0
 0          0         0              0           0         0
 0          0         0.00571026     0.00571026  0         0
 0          0         0.491844       0.491844    0         0
 0          0.170878  0.982952    …  0.982952    0.170878  0
 0          0.659735  1              1           0.659735  0
 0.0590655  0.975524  1              1           0.975524  0.0590655
 0.293527   1         1              1           1         0.293527
 0.445643   1         1              1           1         0.445643
 ⋮                                ⋱                        ⋮
 0.293527   1         1              1           1         0.293527
 0.0590655  0.975524  1              1           0.975524  0.0590655
 0          0.659735  1              1           0.659735  0
 0          0.170878  0.982952    …  0.982952    0.170878  0
 0          0         0.491844       0.491844    0         0
 0          0         0.00571026     0.00571026  0         0
 0          0         0              0           0         0
 0          0         0              0           0         0
 0          0         0           …  0           0         0
```
