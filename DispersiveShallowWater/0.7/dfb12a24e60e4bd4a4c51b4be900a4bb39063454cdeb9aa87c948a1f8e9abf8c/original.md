```
initial_condition_convergence_test(x, t, equations::BBMEquation1D, mesh)
```

A traveling-wave solution used for convergence tests in a periodic domain, here generalized for dimensional variables.

See section 4.1.3 in (there is an error in paper: it should be `sech^2` instead of `cosh`):

  * Hendrik Ranocha, Dimitrios Mitsotakis and David I. Ketcheson (2020) A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
