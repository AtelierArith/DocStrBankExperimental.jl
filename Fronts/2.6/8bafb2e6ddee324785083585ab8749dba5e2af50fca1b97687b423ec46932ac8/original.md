```
solve(::DirichletProblem{<:DiffusionEquation{1}}, ::MathiasAndSander[; maxiters]) -> Solution
```

Solve a Dirichlet problem using the pseudospectral method of Mathias and Sander (2021).

# Keyword arguments

  * `maxiters=100`: maximum number of iterations.

# References

MATHIAS, S. A.; SANDER, G. C. Pseudospectral methods provide fast and accurate solutions for the horizontal infiltration equation. Journal of Hydrology, 2021, vol. 598, p. 126407.

See also: [`MathiasAndSander`](@ref), [`Solution`](@ref)
