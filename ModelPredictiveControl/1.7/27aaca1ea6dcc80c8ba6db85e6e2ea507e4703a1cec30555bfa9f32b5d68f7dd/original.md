```
LinModel{NT}(A, Bu, C, Bd, Dd, Ts)
```

Construct the model from the discrete state-space matrices `A, Bu, C, Bd, Dd` directly.

See [`LinModel(::StateSpace)`](@ref) Extended Help for the meaning of the matrices. The arguments `Bd` and `Dd` can be the scalar `0` if there is no measured disturbance. This syntax do not modify the state-space representation provided in argument (`minreal` is not called). Care must be taken to ensure that the model is controllable and observable. The  optional parameter `NT` explicitly set the number type of vectors (default to `Float64`).
