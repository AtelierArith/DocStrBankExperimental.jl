```
θ2par(θ, model)
```

Function two convert parameter vector to struct

  * `θ`: Parameter vector
  * `model`: Model specification CountModel, INGARCHModel, INARMAModel, ...

Parameter vector needs to be of suitable length.

# Example

```julia-repl
model = Model(pastObs = 1) # Specify INARCH(1)
θ2par([10, 0.5], model)
```
