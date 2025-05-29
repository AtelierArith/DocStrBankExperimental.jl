```julia
predictor(
    bp,
    δp;
    verbose,
    ampfactor,
    nbfailures,
    maxiter,
    perturb,
    J,
    normN,
    optn
)

```

This function provides prediction for what the zeros of the reduced equation / normal form should be for the parameter value `δp`. The algorithm for finding these zeros is based on deflated newton.

## Optional arguments

  * `J` jacobian of the normal form. It is evaluated with ForwardDiff otherwise.
  * `perturb` perturb function used in Deflated newton
  * `normN` norm used for newton.
