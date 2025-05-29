```
jumpratelaw(rx; combinatoric_ratelaw=true)
```

Given a [`Reaction`](@ref), return the symbolic reaction rate law used in generated stochastic chemical kinetics model SSAs for the reaction. Note, for a reaction defined by

`k*X*Y, X+Z --> 2X + Y`

the expression that is returned will be `k*X^2*Y*Z`. For a reaction of the form

`k, 2X+3Y --> Z`

the expression that is returned will be `k * binomial(X,2) * binomial(Y,3)`.

Notes:

  * Allocates
  * `combinatoric_ratelaw=true` uses binomials in calculating the rate law, i.e. for `2S -> 0` at rate `k` the ratelaw would be `k*S*(S-1)/2`. If `combinatoric_ratelaw=false` then the ratelaw is `k*S*(S-1)`, i.e. the rate law is not normalized by the scaling factor.
