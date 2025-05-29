# SAMIN

## Constructor

```julia
SAMIN(; nt::Int = 5     # reduce temperature every nt*ns*dim(x_init) evaluations
        ns::Int = 5     # adjust bounds every ns*dim(x_init) evaluations
        t0::T = 2.0     # Initial temperature
        rt::T = 0.9     # geometric temperature reduction factor: when temp changes, new temp is t=rt*t
        r_expand::T = 10.0 # geometric temperature promotion factor for situation with low coverage: when temp changes, new temp is t=r_expand*t
        bounds_ratio::T = 0.6 # cut-off for bounds increment (1-bounds_ratio for decrease)
        neps::Int = 5   # number of previous best values the final result is compared to
        coverage_ok::Bool = false, # if false, increase temperature until initial parameter space is covered
        verbosity::Int = 1) # scalar: 0, 1, 2 or 3 (default = 1).
```

## Description

The `SAMIN` method implements the Simulated Annealing algorithm for problems with bounds constrains a described in Goffe et. al. (1994) and Goffe (1996). The algorithm

## References

  * Goffe, et. al. (1994) "Global Optimization of Statistical Functions with Simulated Annealing", Journal of Econometrics, V. 60, N. 1/2.
  * Goffe, William L. (1996) "SIMANN: A Global Optimization Algorithm using Simulated Annealing " Studies in Nonlinear Dynamics & Econometrics, Oct96, Vol. 1 Issue 3.
