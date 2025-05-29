Computes the weights in a complete Chebyshev polynomial using multi-threading given the approximation sample,  `y`, the Chebyshev polynomials, `poly` evaluated at the Chebyshev roots, and the `order` of the  polynomial.  Returns a multi-dimensional array containing the weights.  The element-type of the Chebyshev  weights is given by the element-type of `poly`.

# Signature

w = chebyshev*weights*threaded(y,poly,order)

# Example

```
julia> nodes1 = nodes(5,:chebyshev_nodes,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_nodes,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = 3
julia> weights = chebyshev_weights_threaded(y,(poly1.poly,poly2.poly),ord)
[1.66416      0.598458    -0.0237052   0.00272941
  0.26378      0.0948592   -0.00375743  0.0
 -0.0246176   -0.00885287   0.0         0.0
  0.00372291   0.0          0.0         0.0]
```
