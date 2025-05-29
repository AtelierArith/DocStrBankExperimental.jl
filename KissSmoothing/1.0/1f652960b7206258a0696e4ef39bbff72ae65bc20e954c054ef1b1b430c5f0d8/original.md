```
fit_sine_series(X::Vector,Y::Vector, basis_elements::Integer; lambda = 0.0, order=3)
```

fit Y ~ 1 + X + Σ sin(.) by minimising Σ (Y - f(x))^2 + lambda * ∫(Δ^order F)^2

```
`X` : array N, N number of training points.

`Y` : array N, N number of training points.

`basis_elements` : number of sine terms.

Keyword arguments:

`lambda` : intensity of regularization.

`order` : derivative to regularise.
```

returns a callable function.
