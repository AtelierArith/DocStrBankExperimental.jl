```
KnitroSolver(::Val{Bool}, nlp; kwargs...,)
```

Returns a `KnitroSolver` structure to solve the problem `nlp` with `knitro!`.

Knitro does not accept least-squares problems with constraints other than bounds. If an NLSModel has constraints other than bounds, we convert it to a FeasibilityFormNLS. The first argument is `Val(false)` if the problem has been converted, and `Val(true)` otherwise.

For the possible `kwargs`, we refer to `knitro`.
