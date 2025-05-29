```
solve_rachford_rice(K, z, [V]; <keyword arguments>)
```

Compute vapor mole fraction `V` for given equilibrium constants `K` and mole fractions `z`.

# Arguments

`K` - Equal length to `z`, containing the equilibrium constants for each component. `z` - Mole fractions. Should sum up to unity.

# Keyword arguments

  * `tol = 1e-12`: Tolerance for solve.
  * `maxiter=1000`: Maximum number of iterations
  * `ad=false`: Use automatic differentiation (ForwardDiff) instead of analytical gradient.
  * `analytical=true`: Use analytical solutions for 2 and 3 components.

# Examples

```julia-repl
julia> solve_rachford_rice([0.5, 1.5], [0.3, 0.7])
0.8000000000000002
```
