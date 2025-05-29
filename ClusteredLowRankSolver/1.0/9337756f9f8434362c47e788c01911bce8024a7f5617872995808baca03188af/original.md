```
Constraint(constant, matrixcoeff, freecoeff[, samples, scalings])
```

Models a polynomial constaint of the form

$$
    ∑_i ⟨ A_i(x), Y_i  ⟩ + ∑_j b_j(x) y_j = c(x)
$$

using sampling on `samples`. Here the samples are only required if $A_i$, $b_j$, and $c$ are polynomials. When the coefficient matrix $A_i$ has block structure with equal sized blocks, the `Block` struct can be used as key to indicate to which subblock the given matrix corresponds.

Arguments:

  * `constant`: The right hand side $c(x)$
  * `matrixcoeff::Dict`: The coefficient matrices for the positive semidefinite matrix variables.
  * `freecoeff::Dict`: The coefficients for the free variables.
  * `samples::Vector`: The sample set on which the constraint should be satisfied. Required for polynomial constraints.
  * `scalings::Vector`: Optional; scale the constraint with a factor depending on the sample index.
