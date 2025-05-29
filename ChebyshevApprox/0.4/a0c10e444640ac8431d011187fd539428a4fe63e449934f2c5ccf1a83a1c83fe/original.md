Computes the weights in a tensor-product Chebyshev polynomial using multi-threading given the approximation sample,  `y`, the Chebyshev roots, `nodes`, the `order` of the polynomial, and the `domain`.  Returns a  multi-dimensional array containing the weights.  The element-type of the Chebyshev weights is given by the  element-type of the `nodes`.

# Signature

w = chebyshev*weights*threaded(y,nodes,order,domain)

# Example

```
julia> nodes1 = chebyshev_nodes(5,[9.0,3.0])
julia> nodes2 = chebyshev_nodes(5,[1.5,0.5])
julia> y = [nodes1[i]^0.3*nodes2[j]^0.7 for i in 1:5, j in 1:5]
julia> ord = (3,3)
julia> dom = [9.0 1.5; 3.0 0.5]
julia> weights = chebyshev_weights_threaded(y,(nodes1,nodes2),ord,dom)
[1.66416      0.598458    -0.0237052     0.00272941
  0.26378      0.0948592   -0.00375743    0.000432628
 -0.0246176   -0.00885287   0.000350667  -4.03756e-5
  0.00372291   0.00133882  -5.30312e-5    6.10598e-6]
```
