```
RectangularAnnulus(x, y, w_in, w_out, h_out, θ=0)
RectangularAnnulus(position, w_in, w_out, h_out, θ=0)
```

A rectangular annulus with inner width `w_in`, outer width `w_out`, outer height `h_out`, and position angle `θ` in degrees. `h_in` is automatically calculated from `w_in / w_out * h_out`. Note that `w_out ≥ w_in > 0`.

# Examples

```jldoctest
julia> ap = RectangularAnnulus(0, 0, 5, 10, 8, 45)
13×13 RectangularAnnulus{Float64} with indices -6:6×-6:6:
 0.0       0.0       0.0         …  0.0         0.0       0.0
 0.0       0.0       0.0            0.0         0.0       0.0
 0.0       0.0       0.00252532     0.0         0.0       0.0
 0.0       0.0       0.568542       0.0         0.0       0.0
 0.0       0.568542  1.0            0.215729    0.0       0.0
 0.528175  1.0       1.0         …  1.0         0.215729  0.0
 0.215729  1.0       1.0            1.0         1.0       0.215729
 0.0       0.215729  1.0            1.0         1.0       0.528175
 0.0       0.0       0.215729       1.0         0.568542  0.0
 0.0       0.0       0.0            0.568542    0.0       0.0
 0.0       0.0       0.0         …  0.00252532  0.0       0.0
 0.0       0.0       0.0            0.0         0.0       0.0
 0.0       0.0       0.0            0.0         0.0       0.0
```
