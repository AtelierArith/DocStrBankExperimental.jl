```
create_chebyshev_approximation(func::Function, nodes::Integer, degree::Integer, left::Real, right::Real)
```

An function that will approximate another function via Chebyshev polynomials.

### Inputs

  * `func` - A function that you want to approximation
  * `nodes` - The number of approximation nodes
  * `degree` - The degree of the Chebyshev polynomials.
  * `left` - The left limit of the approximation
  * `right` - The right limit of the approximation.

### Returns

  * A `Sum_Of_Functions` containing the approximation function.
