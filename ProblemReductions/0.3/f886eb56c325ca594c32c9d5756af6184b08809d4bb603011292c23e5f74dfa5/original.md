```
AbstractProblem
```

The abstract base type of computational problems.

### Required interfaces

  * [`num_variables`](@ref), the number of variables in the computational problem.
  * [`num_flavors`](@ref), the number of flavors (domain) of a degree of freedom.
  * [`solution_size`](@ref), the size (the lower the better) of the input configuration.
  * [`problem_size`](@ref), the size of the computational problem. e.g. for a graph, it could be `(n_vertices=?, n_edges=?)`.
  * [`energy_mode`](@ref), the definition of the energy function, which can be `LargerSizeIsBetter` or `SmallerSizeIsBetter`.

### Derived interfaces

  * [`variables`](@ref), the degrees of freedoms in the computational problem.
  * [`flavors`](@ref), the flavors (domain) of a degree of freedom.
  * [`findbest`](@ref), find the best configurations of the input problem.
