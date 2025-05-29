```
function kfold(f, df, k, r = 1, shuffle=true; kwargs...)

Provide a simple `k` fold(s) cross-validation, repeated `r` time(s).
`kwargs` arguments are passed to the `regress` function call.
This feature overlap in part with the PRESS statistics.
```
