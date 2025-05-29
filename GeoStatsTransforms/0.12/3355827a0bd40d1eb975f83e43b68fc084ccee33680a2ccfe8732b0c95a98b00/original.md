```
Quenching(transiogram; [options])
```

Simulated quenching (Carle et al. 1998) with given theoretical `transiogram` from GeoStatsFunctions.jl.

## Options

  * `skip`         - Indices to skip during simulation (default to `[]`)
  * `tol`          - Tolerance on relative error (default to `1e-2`)
  * `maxiter`      - Maximum number of iterations (default to `10`)
  * `maxneighbors` - Maximum number of neighbors (default to `26`)
  * `rng`          - Random number generator (default to `Random.default_rng()`)

## Examples

```julia
# simulated quenching with Gaussian transiogram
Quenching(GaussianTransiogram())

# do not change value at first geometry of the domain
Quenching(SphericalTransiogram(), skip=[1])
```

## References

  * Carle et al 1998. [Conditional Simulation of Hydrofacies Architecture: A Transition Probability/Markov Approach](https://doi.org/10.2110/sepmcheg.01.147)
