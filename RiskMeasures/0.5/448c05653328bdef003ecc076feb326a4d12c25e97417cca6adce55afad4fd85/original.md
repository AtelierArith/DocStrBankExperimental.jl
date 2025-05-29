```
ERM(x̃, β [, x̃min, check_inputs = true])
```

Compute the entropic risk measure of the random variable `x̃` with risk level `β`. 

The optional `x̃min` parameter is used as an offset in order to avoid overflows when computing the exponential function. If not provided, the minimum value of `x̃` is used instead. 

Assumes a maximization problem. Using `β=0` computes expectation and `β=Inf` computes the essential infimum (smallest value with positive probability).

More details: [https://en.wikipedia.org/wiki/Entropic_risk_measure](https://en.wikipedia.org/wiki/Entropic_risk_measure)
