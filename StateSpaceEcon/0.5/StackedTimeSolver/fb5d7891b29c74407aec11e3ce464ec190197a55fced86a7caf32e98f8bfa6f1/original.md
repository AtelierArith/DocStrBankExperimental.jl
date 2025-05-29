```
setfc(model, fc)
```

Return a vector of final conditions for all variables in the `model`. The final conditions of all variables are set to `fc`, except shocks and exogenous, which are always `fcnone`. Use [`setfc!`](@ref) to update the final condition of individual variable.
