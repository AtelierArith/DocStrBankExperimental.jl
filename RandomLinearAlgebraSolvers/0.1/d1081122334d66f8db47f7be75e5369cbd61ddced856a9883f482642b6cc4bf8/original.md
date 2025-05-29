```
stp = RLAStopping(A, b::S; n_listofstates::Int = 0, kwargs...)
```

Creator of a `LAStopping` tailored for this package. The problem, stp.pb, is a `Stopping.LinearSystem` if `A` is dense, and a `LLSModels.LLSModel` otherwise. The state allocates space for the residual, `stp.current_state.res`, of length `|b|`. This stopping uses the infinity norm of `stp.current_state.res` to declare optimality.
