```
partial_linearsystem(problem::Problem, sol::DualSolution, columns::Union{DualSolution, Vector{Int}})
```

Let x be the vcat of the vectorizations of the matrix variables. Let I be the index set of the columns. This function returns the matrix A*I and vector b-Ax such that the constraints for  the error vector e using variables indexed by I are given by the system A*Ie = b-Ax.
