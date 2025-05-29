```
loglikelihood(v::IHTVariable{T, M})
```

Calculates the loglikelihood of observing `y` given mean `μ = E(y) = g^{-1}(xβ)` and some univariate distribution `d`. 

Note that loglikelihood is the sum of the logpdfs for each observation. 
