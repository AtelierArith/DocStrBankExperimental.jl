```julia
balancematrix(equation::ChemEquations.ChemEquation) -> Any

```

Balances an equation matrix using the *nullspace method*. Returns an array in which each column represents a solution.

# References

  * [Thorne (2009)](https://arxiv.org/ftp/arxiv/papers/1110/1110.4321.pdf)
