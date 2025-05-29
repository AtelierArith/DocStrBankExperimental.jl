```
expand(expr)
```

Expand expressions by distributing multiplication over addition, e.g., `a*(b+c)` becomes `ab+ac`.

`expand` uses replace symbols and non-algebraic expressions by variables of type `variable_type` to compute the distribution using a specialized sparse multivariate polynomials implementation. `variable_type` can be any subtype of `MultivariatePolynomials.AbstractVariable`.
