```
logsumexp(x; dims = :)
```

Computes `log.(sum(exp.(x); dims))` in a numerically stable way. Without `dims` keyword this returns a scalar.

See also [`logsoftmax`](@ref).
