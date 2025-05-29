```
bootstrap!(problem::FRACProblem; nboot = 100, ndraws = 100, approximate = false)
```

This function bootstraps the parameters of a FRAC problem. It does so by resampling the residuals ξ and  re-simulating market shares repeatedly. The function modifies the `problem` object in place, adding the  bootstrapped parameters (a vector of dictionaries including all bootstrap) to the `bootstrapped\_parameters\_all` field and the debiased parameters to the  `bootstrap\_debiased\_parameters` field. The latter is calculated via the following: 

`bootstrap\_debiased\_parameters` = 2 β - 1/B sum(β^b)

where β is the original estimate and β^b is the estimate from the bth bootstrap sample.
