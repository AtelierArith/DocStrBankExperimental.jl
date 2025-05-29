```
getdetJdV(fe_v::AbstractValues, q_point::Int)
```

Return the product between the determinant of the Jacobian and the quadrature point weight for the given quadrature point: $\det(J(\mathbf{x})) w_q$.

This value is typically used when one integrates a function on a finite element cell or facet as

$\int\limits_\Omega f(\mathbf{x}) d \Omega \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) \det(J(\mathbf{x})) w_q$ $\int\limits_\Gamma f(\mathbf{x}) d \Gamma \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) \det(J(\mathbf{x})) w_q$
