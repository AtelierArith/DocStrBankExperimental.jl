```
jacobian(F::System)
```

Computes the symbolic Jacobian of the system `F`.

# Example

```julia
@var x y
F = System([x^2 + 3y, (y*x+1)^3])
jacobian(F)
```

```
2×2 Array{Expression,2}:
             2*x                3
 3*y*(1 + x*y)^2  3*x*(1 + x*y)^2
```
