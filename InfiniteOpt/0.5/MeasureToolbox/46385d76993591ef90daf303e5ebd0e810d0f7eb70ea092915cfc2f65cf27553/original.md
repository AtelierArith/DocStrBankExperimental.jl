```
GaussHermite <: AbstractUnivariateMethod
```

An integral evaulation method that uses Gauss-Hermite quadrature to evaluate integrals. This is valid for infinite integral domains.  It will take this form:

$\int_{-∞}^{∞} f(x) e^{-x^2} \approx \sum_{i=1}^{n} \alpha_i f(x_i)$

Using the weight function: $w(x)$ = $e^{-x^2}$

Note this will generate its own set of supports and will ignore other parameter supports. This is not compatible with individual dependent parameters.
