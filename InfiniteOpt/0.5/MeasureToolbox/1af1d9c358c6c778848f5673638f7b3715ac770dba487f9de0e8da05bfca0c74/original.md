```
FEGaussLobatto <: AbstractUnivariateMethod
```

Integral evaluation method that allows for the user to specify supports to be included in quadrature evaluation. The upper and lower bounds of the integral will automatically  be added as supports. This method uses Gauss Lobatto quadrature to decompose the overall Integral into smaller integrals that span the user defined supports as follows:

$\int_{x_1}^{x_3} f(x) dx = \int_{x_1}^{x_2} f(x) dx + \int_{x_2}^{x_3} f(x) dx$

where the integrals are evaluated using Gauss Lobatto quadrature:

$\int f(x) dx \approx \sum_{i=1}^{n} \alpha_i f(x_i)$
