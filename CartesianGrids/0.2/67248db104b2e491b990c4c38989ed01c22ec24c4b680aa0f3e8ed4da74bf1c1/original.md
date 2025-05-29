```
plan_helmholtz(dims::Tuple,α::Number,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0],[dx=1.0])
```

Constructor to set up an operator for evaluating the discrete Helmholtz operator on complex dual or primal nodal data of dimension `dims`. If the optional keyword `with_inverse` is set to `true`, then it also sets up the inverse Helmholtz operator (the lattice Green's function, LGF). These can then be applied, respectively, with `*` and `\` operations on data of the appropriate size. The optional parameter `factor` is a scalar used to multiply the result of the operator and divide the inverse. The optional parameter `dx` is used in adjusting the uniform value of the LGF to match the behavior of the continuous analog at large distances; this is set to 1.0 by default.

Instead of the first argument, one can also supply `w::Nodes` to specify the size of the domain.

# Example
