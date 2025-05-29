```
BetaFourParameters
```

  * Parametrization a, c, \alpha, \beta
  * Score
  * Fisher Information
  * `time_varying_params` map.
  * Default link

Right now when estimating a BetaFourParameters model is recomended to provide fixed parameters a and c, dont with the code:

```julia
gas_beta_4 = ScoreDrivenModel([1, 2, 11, 12], [1, 2, 11, 12], BetaFourParameters, 0.0; time_varying_params=[3])
gas_beta_4.ω[1] = minimum(y) - 0.1*std(y) # parameter a
gas_beta_4.ω[2] = maximum(y) + 0.1*std(y) # parameter c
```

This code is a simple and not very accurate heuristic on how to estimate the a and c parameters. If you have estimated using maximum likelihood it will be probably better

The fact occurs because if in the optimization the gradient makes `c < maximum(y)` or `a > minimum(y)` then it is impossible that y comes from the BetaFourParameters distribution leading to DomainErrors
