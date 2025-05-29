```
GaussChebyshev <: FiniteGaussQuad
```

An integral evaulation method that uses Gauss-Chebyshev quadrature to evaluate integrals. This is valid for finite integral domains. This requires the user to input the order of Guass-Chebyshev Quadrature they want to use.  If the order is not between 1 and 4 an error will be returned.  The integral evaluated is as follows:

$\int_{-1}^{1} f(x) w(x) \approx \sum_{i=1}^{n} \alpha_i f(x_i)$

The weight functions are as follows: 

  * 1st order: $w(x)  =  \frac{1}{\sqrt{1-x^2}}$
  * 2nd order: $w(x) = {\sqrt{1-x^2}}$
  * 3rd order: $w(x) = \sqrt{(1+x)/(1-x)}$
  * 4th order: $w(x) = \sqrt{(1-x)/(1+x)}$

This will then generate its own set of supports and will ignore other parameter supports. This is not compatible with individual dependent parameters.

**Fields**

  * `order::Int`: Specifies the order of Gauss-Chebyshev Quadrature. Must be between 1 and 4.
