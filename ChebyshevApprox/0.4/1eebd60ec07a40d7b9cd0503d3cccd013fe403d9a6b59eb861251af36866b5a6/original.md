Computes the second derivative of the Chebyshev polynomial of `order` at the scalar `x`, which must lie in [1.0,-1.0].  Returns a 2d array.  The element-type of the polynomial is given by the element-type of `x`.

# Signature

P = chebyshev*polynomial*sec_deriv(order,x)

# Example

```
julia> P = chebyshev_polynomial_sec_deriv(3,0.6)
[0.0  0.0  4.0  14.4]
```
