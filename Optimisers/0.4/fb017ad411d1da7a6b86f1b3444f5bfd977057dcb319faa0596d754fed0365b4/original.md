```
ClipGrad(δ = 10)
ClipGrad(; [delta])
```

Restricts every gradient component to obey `-δ ≤ dx[i] ≤ δ`.

Typically composed with other rules using [`OptimiserChain`](@ref).

See also [`ClipNorm`](@ref).
