```julia
d_criterion(model_matrix; tolerance) -> Any

```

Criterion of D-optimality, which seeks to minimize $|(X^T · X) − I*tol| / N^{1/b}$, or equivalently maximize the determinant of the information matrix $X^T · X$ of the design. This criterion results in maximizing the differential Shannon information content of the parameter estimates.
