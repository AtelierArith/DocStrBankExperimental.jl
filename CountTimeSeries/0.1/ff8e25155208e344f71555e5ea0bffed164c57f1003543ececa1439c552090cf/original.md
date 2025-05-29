```
par2θ(θ, model)
```

Function two convert parameter struct to vector

  * `θ`: Parameter struct
  * `model`: Model specification CountModel, INGARCHModel, ...

# Example

```julia-repl
model = CountModel(past_obs = 1) # Specify INARCH(1)
pars = θ2par([10, 0.5], model)
θ = par2θ(pars, model)
```
