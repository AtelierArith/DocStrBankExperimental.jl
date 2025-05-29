Computes the Chebyshev polynomial of degree `order` at end point in the vector `x`. The elements of `x` must lie in [1.0,-1.0].  Returns a 2d array.  The element-type of the polynomial is given by the element-type of  `x`.

# Signature

P = chebyshev_polynomial(order,x)

# Example

```
julia> P = chebyshev_polynomial(3,[0.6,0.4])
[1.0  0.6  -0.28  -0.936
 1.0  0.4  -0.68  -0.944]
```
