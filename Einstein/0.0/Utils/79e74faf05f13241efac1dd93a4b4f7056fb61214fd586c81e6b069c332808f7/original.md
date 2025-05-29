```
barycentric_weights(x::AbstractVector{TF}) where {TF<:AbstractFloat}
barycentric_weights(x::AbstractRange{TF}) where {TF<:AbstractFloat}
barycentric_weights([TF=Float64], order::Integer) where {TF<:AbstractFloat}
```

Compute normalized barycentric weights for interpolation nodes. These weights are used in barycentric Lagrange interpolation. For Chebyshev-Gauss nodes or Chebyshev-Lobatto nodes, [cheb*gauss*barycentric_weights](@ref Einstein.ChebyshevSuite.cheb_gauss_barycentric_weights) and [cheb*lobatto*barycentric_weights](@ref Einstein.ChebyshevSuite.cheb_lobatto_barycentric_weights) are more efficient implementations.

# Arguments

  * `x::AbstractVector{TF}`: Vector of distinct interpolation nodes, for equidistant nodes, use range is recommended `x = x_min:dx:x_max`
  * `order::Integer`: order of the interpolation (order = length(x) - 1)

# Returns

  * `Vector{TF}`: Barycentric weights scaled such that their infinity norm equals 1

# Details

The barycentric weights $w_j$ for nodes $x_j$ are computed as:

$$
w_j = \frac{1}{\prod_{k \neq j} (x_j - x_k)}
$$

For equidistant nodes, a more efficient formula is used based on binomial coefficients.

# Examples

```julia
# For arbitrary nodes
x = [0.0, 1.0, 2.0]
w = barycentric_weights(x)

# For equidistant nodes
w = barycentric_weights(2)  # 3 nodes: 0, 1, 2

# or
x = 0.0:0.1:1.0
w = barycentric_weights(x)
```

# Notes

  * The weights are scaled to have unit infinity norm for numerical stability
  * Returns NaN weights if input points are not distinct
  * log-sum-exp trick is used to prevent underflow/overflow
  * For equidistant nodes, a more efficient algorithm based on binomial coefficients is used

# References

  * [Berrut2004](@citet*)
  * [chebfun/baryWeights.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/baryWeights.m)
