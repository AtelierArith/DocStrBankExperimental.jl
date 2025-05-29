```
rosenbrock(x; b=100)
```

!!! compat "Changed since EvoLP 1.3"
    This is the $d$-dimensional Rosenbrock function. In previous releases, it was 2d only and had an additional keyword argument `a`.

    Update your workflow accordingly.


The $d$-dimensional **Rosenbrock** *banana* benchmark function. With $b=100$, minimum is at $f([1, \dots, 1]) = 0$

$$
f(x) = \sum_{i=1}^{d-1} \left[b(x_{i+1} - x_i^2)^2 + (x_i - 1)^2 \right]
$$
