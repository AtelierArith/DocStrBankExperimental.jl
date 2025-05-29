Computes the weights in a tensor-product Chebyshev polynomial given the approximation sample, `y`, the Chebyshev polynomials, `poly` evaluated at the Chebyshev extrema, and the `order` of the polynomial.  Returns a  multi-dimensional array containing the weights.  The element-type of the Chebyshev weights is given by the  element-type of `poly`.

# Signature

w = chebyshev*weights*extrema(y,poly,order)

# Example

```
julia> nodes1 = nodes(5,:chebyshev_extrema,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_extrema,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> weights = chebyshev_weights_extrema(y,(poly1.poly,poly2.poly),ord)
[1.66416      0.598461   -0.02372       0.00280618
  0.263786     0.0948622  -0.00375987    0.000444808
 -0.024647    -0.0088635   0.000351305  -4.15608e-5
  0.00386243   0.001389   -5.5053e-5     6.513e-6]
```
