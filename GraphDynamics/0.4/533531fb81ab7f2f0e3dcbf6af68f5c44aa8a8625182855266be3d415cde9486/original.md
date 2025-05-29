```
isstochastic(::Type{T})
```

Defaults to `false`, but for subsystems which define a stochastic differential equation, you must add a method to this function of the form

```
GraphDynamics.isstochastic(::Type{Mytype}) = true
```
