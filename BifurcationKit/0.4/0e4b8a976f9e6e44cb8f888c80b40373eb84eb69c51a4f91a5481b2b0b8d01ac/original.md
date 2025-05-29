```julia
predictor(
    bp,
    ,
    δp;
    verbose,
    ampfactor,
    nbfailures,
    maxiter,
    perturb,
    J,
    igs,
    normN,
    optn
)

```

This function provides prediction for what the zeros of the reduced equation / normal form should be should be for the parameter value `δp`. The algorithm for finding these zeros is based on deflated newton. The initial guesses are the vertices of the hypercube.

## Optional arguments

  * `J` jacobian of the normal form. It is evaluated with ForwardDiff otherwise.
  * `perturb` perturb function used in Deflated newton
  * `normN` norm used for newton.
  * `igs` vector of initial guesses. If not passed, these are the vertices of the hypercube.
