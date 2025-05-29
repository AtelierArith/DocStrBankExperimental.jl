Computes the weights in a tensor-product Chebyshev polynomial given the approximation sample, `y`, the Chebyshev polynomials, `poly` evaluated at the extended Chebyshev points, and the `order` of the polynomial.  Returns a  multi-dimensional array containing the weights.  The element-type of the Chebyshev weights is given by the  element-type of `poly`.

# Signature

w = chebyshev*weights*extended(y,poly,order)

# Example

```
julia> nodes1 = nodes(5,:chebyshev_extended,[9.0,3.0])
julia> nodes2 = nodes(5,:chebyshev_extended,[1.5,0.5])
julia> poly1 = chebyshev_polynomial(3,nodes1)
julia> poly2 = chebyshev_polynomial(3,nodes2)
julia> y = [nodes1.points[i]^0.3*nodes2.points[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> weights = chebyshev_weights_extended(y,(poly1.poly,poly2.poly),ord)
[1.66393      0.598444    -0.0238922     0.00277041
  0.263837     0.0948909   -0.00378841    0.000439284
 -0.0249247   -0.00896435   0.000357891  -4.14991e-5
  0.00379791   0.00136595  -5.45338e-5    6.32345e-6]
```
