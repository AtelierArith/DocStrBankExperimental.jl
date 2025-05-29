```
gamma = PolynomialStepSize(eta::AbstractFloat, [c::AbstractFloat=1.0]))
```

Constructor for PolynomialStepSize.

# Arguments

  * `eta`: The step size exponent, should be within (1/2,1].
  * `c`: Scaling factor; default `1.0`.
