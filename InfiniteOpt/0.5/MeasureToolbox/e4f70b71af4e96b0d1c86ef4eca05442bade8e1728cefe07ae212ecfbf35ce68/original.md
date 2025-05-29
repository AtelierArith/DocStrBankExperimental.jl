```
GaussJacobi <: FiniteGaussQuad
```

An integral evaulation method that uses Gauss-Jacobi quadrature to evaluate integrals. It will take this form:

$\int_{-1}^{1} f(x) (1-x)^\alpha (1+x)^\beta dx \approx \sum_{i=1}^{n} \alpha_i f(x_i)$

Where, 

$(1-x)^\alpha (1+x)^\beta$ 

is the weight function. This is valid for finite integral domains. This requires the user to input the alpha and beta shape parameters for their function. This will then generate its own set of supports and will ignore other parameter supports. This is not compatible with individual dependent parameters. If α or β is < -1, an error will be returned.  

**Fields**

  * `α::Float64`: Shape parameter that must be > -1
  * `β::Float64`: Shape parameter that must be > -1
