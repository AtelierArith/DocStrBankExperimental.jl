Computes the Chebyshev polynomial of degree `order` at the scalar point `x`, which must lie in [1.0,-1.0]. Returns a 2d array.  The element-type of the polynomial is given by the element-type of `x`.

# Signature

P = chebyshev_polynomial(order,x)

# Example

```
julia> P = chebyshev_polynomial(3,0.6)
[1.0  0.6  -0.28  -0.936]
```
