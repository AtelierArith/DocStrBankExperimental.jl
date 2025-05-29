Computes the weights in a complete Chebyshev polynomial using multi-threading given the approximation sample,  `y`, the extended Chebyshev points, `nodes`, the `order` of the polynomial, and the `domain`. Returns a multi-dimensional array containing the weights.  The element-type of the Chebyshev weights is given by the element-type of the `nodes`.

# Signature

w = chebyshev*weights*extended_threaded(y,nodes,order,domain)

# Example

```
julia> nodes1 = chebyshev_extended(5,[9.0,3.0])
julia> nodes2 = chebyshev_extended(5,[1.5,0.5])
julia> y = [nodes1[i]^0.3*nodes2[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = 3
julia> dom = [9.0 1.5; 3.0 0.5]
julia> weights = chebyshev_weights_extended_threaded(y,(nodes1,nodes2),ord,dom)
[1.66393      0.598444    -0.0238922   0.00277041
  0.263837     0.0948909   -0.00378841  0.0
 -0.0249247   -0.00896435   0.0         0.0
  0.00379791   0.0          0.0         0.0]
```
