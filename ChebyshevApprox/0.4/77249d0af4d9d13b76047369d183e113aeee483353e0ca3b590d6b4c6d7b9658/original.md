Computes the weights in a tensor-product Chebyshev polynomial using multi-threading given the approximation sample, `y`, the Chebyshev extrema, `nodes`, the `order` of the polynomial, and the `domain`.  Returns a  multi-dimensional array containing the weights.  The element-type of the Chebyshev weights is given by the  element-type of the `nodes`.

# Signature

w = chebyshev*weights*extrema_threaded(y,nodes,order,domain)

# Example

```
julia> nodes1 = chebyshev_extrema(5,[9.0,3.0])
julia> nodes2 = chebyshev_extrema(5,[1.5,0.5])
julia> y = [nodes1[i]^0.3*nodes2[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> weights = chebyshev_weights_extrema_threaded(y,(nodes1,nodes2),ord,dom)
[1.66416      0.598461   -0.02372       0.00280618
  0.263786     0.0948622  -0.00375987    0.000444808
 -0.024647    -0.0088635   0.000351305  -4.15608e-5
  0.00386243   0.001389   -5.5053e-5     6.513e-6]
```
