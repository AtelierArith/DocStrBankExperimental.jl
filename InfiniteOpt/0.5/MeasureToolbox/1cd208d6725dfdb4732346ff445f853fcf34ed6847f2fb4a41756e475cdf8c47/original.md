```
GaussLaguerre <: AbstractUnivariateMethod
```

An integral evaulation method that uses Gauss-Laguerre quadrature to evaluate integrals. This is valid for semi-infinite integral domains. 

This method evaluates the following integral:

$\int_{0}^{+∞} f(x) e^{-x} \approx \sum_{i=1}^{n} \alpha_i f(x_i)$

Using the weight function:

$w(x) = e^{-x}$

Note this will generate its own set of supports and will ignore other parameter supports. This is not compatible with individual dependent parameters.
