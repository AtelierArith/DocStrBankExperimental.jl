```julia
guess_from_hopf(
    br,
    ind_hopf,
    eigsolver,
    M,
    amplitude;
    phase
)

```

This function returns several useful quantities regarding a Hopf bifurcation point. More precisely, it returns:

  * the parameter value at which a Hopf bifurcation occurs
  * the period of the bifurcated periodic orbit
  * a guess for the bifurcated periodic orbit
  * the equilibrium at the Hopf bifurcation point
  * the eigenvector at the Hopf bifurcation point.

The arguments are

  * `br`: the continuation branch which lists the Hopf bifurcation points
  * `ind_hopf`: index of the bifurcation branch, as in `br.specialpoint`
  * `eigsolver`: the eigen solver used to find the eigenvectors
  * `M` number of time slices in the periodic orbit guess
  * `amplitude`: amplitude of the periodic orbit guess
