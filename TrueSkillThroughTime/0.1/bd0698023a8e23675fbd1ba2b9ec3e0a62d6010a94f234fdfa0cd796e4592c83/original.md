The `Gaussian` class is used to define the prior beliefs of the agents' skills (and for internal computations).

We can create objects by passing the parameters in order or by mentioning the names. 

```
Gaussian(mu::Float64=MU, sigma::Float64=SIGMA)
Gaussian(;mu::Float64=MU, sigma::Float64=SIGMA)
```

  * `mu` is the mean of the Gaussian distribution
  * `sigma` is the standar deviation of the Gaussian distribution
