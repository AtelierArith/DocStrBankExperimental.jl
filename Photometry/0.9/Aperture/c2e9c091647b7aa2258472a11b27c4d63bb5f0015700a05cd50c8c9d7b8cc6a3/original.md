```
EllipticalAnnulus(x, y, a_in, a_out, b_out, θ=0)
EllipticalAnnulus(position, a_in, a_out, b_out, θ=0)
```

An elliptical annulus with inner semi-major axis `a_in`, outer semi-major axis `a_out`, outer semi-minor axis `b_out`, and position angle `θ`. `a_out` ≥ `a_in` ≥ 0 and `b_out` must be ≥ 0, `θ` is measured in degrees counter-clockwise the standard x-axis.

`b_in` will automatically be calculated from `(a_in / a_out) * b_out`. Note this may cause a type instability.

# Examples

```jldoctest
julia> ap = EllipticalAnnulus(0, 0, 4, 10, 5, 45)
15×15 EllipticalAnnulus{Float64} with indices -7:7×-7:7:
 0.594853   1.0       1.0       1.0         …  0.0       0.0       0.0
 1.0        1.0       1.0       1.0            0.0       0.0       0.0
 1.0        1.0       1.0       1.0            0.0       0.0       0.0
 1.0        1.0       1.0       1.0            0.0       0.0       0.0
 1.0        1.0       1.0       1.0            0.0       0.0       0.0
 0.814163   1.0       1.0       1.0         …  0.414163  0.0       0.0
 0.369432   1.0       1.0       1.0            0.975704  0.193728  0.0
 0.0112571  0.809079  1.0       1.0            1.0       0.809079  0.0112571
 0.0        0.193728  0.975704  1.0            1.0       1.0       0.369432
 0.0        0.0       0.414163  1.0            1.0       1.0       0.814163
 0.0        0.0       0.0       0.546165    …  1.0       1.0       1.0
 0.0        0.0       0.0       0.00252321     1.0       1.0       1.0
 0.0        0.0       0.0       0.0            1.0       1.0       1.0
 0.0        0.0       0.0       0.0            1.0       1.0       1.0
 0.0        0.0       0.0       0.0            1.0       1.0       0.594853
```
