```
integrateOnSimplex(f, S; dim, maxEvals, absError, tol, rule, info, fkwargs...)
```

Integration of a function over one or more simplices.

# Arguments

  * `f`: function to be integrated; must return a real scalar value or a real vector
  * `S`: simplex or vector of simplices; a simplex is given by n+1 vectors of dimension n
  * `dim`: number of components of `f`
  * `maxEvals`: maximum number of calls to `f`
  * `absError`: requested absolute error
  * `tol`: requested relative error
  * `rule`: integration rule, an integer between 1 and 4; a 2*rule+1 degree integration rule is used
  * `info`: Boolean, whether to print more info
  * `fkwargs`: keywords arguments of `f`
