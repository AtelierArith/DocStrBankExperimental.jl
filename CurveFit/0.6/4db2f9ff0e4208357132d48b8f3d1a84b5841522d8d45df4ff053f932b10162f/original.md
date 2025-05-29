# Nonlinear multi-variable least squares

Uses a Newton like algorithm to compute the least squares fit  of a model

## Parameters:

  * `x` an array where each colum is a variable
  * `fun` The function that should be fitted (more later on)
  * `a0` An initial guess for each fitting parameter
  * `eps` Convergence criterion
  * `maxiter` Maximum number of iterations

## Specifying the model

The model is specified in argument `fun` that should be callable according to the following signature:

`r = fun(x, a)`

where both `x` and `a` are vectors

The way the algorithm is implemented allows for the function to be implicit. This means that we are trying to fit the relationship `fun(x, a) = 0`. 

## Initial guess

The initial guess is important and should be as close as possible to the expeted values. It should, at least, give an order of magnitude of each parameter. Zero values are not recommended since in this  case no order of magnitude is available and it is assumed. The initial step is assumed to be `a0/10`.

## Convergence criterion

The initial guess `a0` will probably not fit the data very well. The largest value of `maxerr = maxabs(fun(x, a0))` (maximum error) is used as a reference and  every time a new approximation is computed, if the change in paramaters is compared to this reference error. If it is small, `maxabs(da) < eps*maxerr`, the algorithm converged.

## Return values

A tuple containing:

  * The estimated coefficients
  * A `Bool` stating whether the algorithm converged
  * Number of iterations it took to converge.
