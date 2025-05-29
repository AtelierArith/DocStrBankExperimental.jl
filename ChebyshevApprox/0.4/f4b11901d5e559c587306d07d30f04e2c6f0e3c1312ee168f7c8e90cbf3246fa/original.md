Evaluate a tensor-product Chebyshev polynomial at point, `x``, given the`$weights$`the`$order$`of the polynomial, and the`$domain$`.

# Signature

yhat = chebyshev_evaluate(weights,x,order,domain)

# Example

```
julia> weights = [1.66416      0.598458    -0.0237052     0.00272941
  0.26378      0.0948592   -0.00375743    0.000432628
 -0.0246176   -0.00885287   0.000350667  -4.03756e-5
  0.00372291   0.00133882  -5.30312e-5    6.10598e-6]
julia> x = [5.5,0.9]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> yhat = chebyshev_evaluate(weights,x,ord,dom)
1.5500018804115083
```
