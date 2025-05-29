```julia
ProcessNoiseSystemMap(prob, n, args...; kwargs...)
```

Representation of a system solution map for a given `prob::SDEProblem`. `args` and `kwargs` are forwarded to the equation solver. `n` is the number of terms in the Kosambi–Karhunen–Loève representation of the process noise.
