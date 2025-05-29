```
sorptivity(::InverseProblem)
```

Calculate the sorptivity of a solution to a semi-infinite one-dimensional nonlinear diffusion problem, where the solution is given as a set of discrete points.

Uses numerical integration.

# Arguments

  * `prob::InverseProblem`: inverse problem. See [`InverseProblem`](@ref).

# Keyword arguments

  * `i=nothing`: initial value. If `nothing`, the initial value is taken from `u[end]`.
  * `b=nothing`: boundary value. If `nothing`, the boundary value is taken from `u[begin]`.
  * `ob=0`: value of `o` at the boundary.

# References

PHILIP, J. R. The theory of infiltration: 4. Sorptivity and algebraic infiltration equations. Soil Science, 1957, vol. 83, no. 5, p. 345-357.
