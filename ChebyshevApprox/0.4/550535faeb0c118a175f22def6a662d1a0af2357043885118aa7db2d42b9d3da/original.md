Computes the second derivative of the Chebyshev polynomial of `order` at each point specified in the `nodes` struct.  The elements of `nodes.points` must lie in [1.0,-1.0].  Returns a ChebPoly type.  The element-type of  the polynomial is given by the element-type of `x`.

# Signature

P = chebyshev*polynomial*sec_deriv(order,x)

# Example

```
julia> n = nodes(2,:chebyshev_nodes)
ChebRoots{Float64, Float64}([-0.7071067811865476, 0.7071067811865476], [1.0, -1.0])

julia> P = chebyshev_polynomial_sec_deriv(3,n)
ChebPoly{Float64}([0.0 0.0 4.0 -16.970562748477143; 0.0 0.0 4.0 16.97056274847714], ChebRoots{Float64, Float64})
```
