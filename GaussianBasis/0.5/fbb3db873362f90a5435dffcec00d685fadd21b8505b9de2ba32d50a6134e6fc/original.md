```
 CartesianShell
```

Object holding basis function information for an Cartesian Shell.

# Fields

| Name   | Description                                                      |
|:------ |:---------------------------------------------------------------- |
| `l`    | Pseudo-angular momentum number l = a+b+c for xᵃyᵇzᶜ              |
| `coef` | Array holding expansion coefficients for the primitive functions |
| `exp`  | Array holding exponents for primitive functions                  |

# Examples

```julia
julia> χ = CartesianShell(2, [1/√2], [5.0])
D shell with 6 basis built from 1 primitive gaussians

χ(x²) =    0.7071067812⋅x²⋅exp(-5.0⋅r²)

χ(xy) =    0.7071067812⋅xy⋅exp(-5.0⋅r²)

χ(xz) =    0.7071067812⋅xz⋅exp(-5.0⋅r²)

χ(y²) =    0.7071067812⋅y²⋅exp(-5.0⋅r²)

χ(yz) =    0.7071067812⋅yz⋅exp(-5.0⋅r²)

χ(z²) =    0.7071067812⋅z²⋅exp(-5.0⋅r²)
```
