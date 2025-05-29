```
jacobian(F::System, x, p = nothing)
```

Evaluates the Jacobian of the system `F` at `(x, p)`.

# Example

```julia
@var x y
F = System([x^2 + 3y, (y*x+1)^3])
jacobian(F, [2, 3])
```

```
2×2 Array{Int32,2}:
   4    3
 441  294
```
