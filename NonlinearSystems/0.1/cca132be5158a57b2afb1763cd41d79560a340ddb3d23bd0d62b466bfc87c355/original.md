```
Hybrid{P} <: AbstractAlgorithm{P}
```

A modified version of Powell's hybrid method (a trust region method with dogleg). The essentially same algorithm can solve both root-finding problems and least-squares problem. To indicate the problem type, set either `RootFinding` or `LeastSquares` as type parameter. For keyword arguments accepted by `init` and `solve` when using this algorithm, see [`HybridSolver`](@ref).

# References

  * **Moré, Jorge J., Danny C. Sorenson, Burton S. Garbow, and Kenneth E. Hillstrom.** 1984. "The MINPACK Project." In *Sources and Development of Mathematical Software*, ed. Wayne R. Cowell, 88-111. New Jersey: Prentice-Hall.
  * **Nocedal, Jorge, and Stephen J. Wright.** 2006. *Numerical Optimization.* 2nd ed. New York: Springer.
  * **Powell, Michael J. D.** 1970. "A Hybrid Method for Nonlinear Equations." In *Numerical Methods for Nonlinear Algebraic Equations*, ed. Philip Rabinowitz, 87-114. London: Gordon and Breach.
