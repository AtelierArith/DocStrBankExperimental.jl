```
solve(prob::DirichletProblem[, alg::BoltzmannODE; abstol, maxiters, d_dob_hint, verbose]) -> Solution
```

Solve the problem `prob`.

# Arguments

  * `prob`: problem to solve.
  * `alg=BoltzmannODE()`: algorithm to use.

# Keyword arguments

  * `abstol=1e-3`: absolute tolerance for the initial condition.
  * `maxiters=100`: maximum number of iterations.
  * `verbose=true`: whether warnings are emitted if solving is unsuccessful.

# References

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. Open-source high-performance software packages for direct and inverse solving of horizontal capillary flow. Capillarity, 2023, vol. 6, no. 2, p. 31-40.

See also: [`Solution`](@ref), [`BoltzmannODE`](@ref)
