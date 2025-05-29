```
ClipNorm(ω = 10, p = 2; throw = true)
```

Scales any gradient array for which `norm(dx, p) > ω` to stay at this threshold (unless `p==0`).

Throws an error if the norm is infinite or `NaN`, which you can turn off with `throw = false`.

Typically composed with other rules using [`OptimiserChain`](@ref).

See also [`ClipGrad`](@ref).
