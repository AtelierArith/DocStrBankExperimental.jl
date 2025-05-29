Computes the Chebyshev polynomial of degree `order` at each point specified in the `nodes` struct.  The  elements of `nodes.points` must lie in [1.0,-1.0].  Returns a ChebPoly type.  The element-type of the polynomial is given by the element-type of `x`.

# Signature

P = chebyshev_polynomial(order,x)

# Example

```
julia> n = nodes(2,:chebyshev_nodes)
ChebRoots{Float64, Float64}([-0.7071067811865476, 0.7071067811865476], [1.0, -1.0])

julia> P = chebyshev_polynomial(3,n)
ChebPoly{Float64}([1.0 -0.7071067811865476 2.220446049250313e-16 0.7071067811865472; 1.0 0.7071067811865475 -2.220446049250313e-16 -0.7071067811865478], ChebRoots{Float64, Float64})
```
