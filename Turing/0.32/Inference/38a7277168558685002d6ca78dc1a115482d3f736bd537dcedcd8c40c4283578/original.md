```
PolynomialStepsize(a[, b=0, γ=0.55])
```

Create a polynomially decaying stepsize function.

At iteration `t`, the step size is

$$
a (b + t)^{-γ}.
$$
