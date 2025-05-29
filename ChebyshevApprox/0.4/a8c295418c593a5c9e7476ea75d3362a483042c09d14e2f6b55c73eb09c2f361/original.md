Computes `N` roots with floating point type `T` of the Chebyshev polynomial and scales the roots to the  interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` Chebyshev roots with type `T` located over the specified domain.

# Signature

points = chebyshev_nodes(T,N,domain)

# Examples

```
julia> using DoubleFloats
julia> points = chebyshev_nodes(Float64,2)
[-4.1421356237309504880168872420969394e-01
  2.41421356237309504880168872420969394]

julia> points = chebyshev_nodes(Double64,2,[3.0,-1.0])
[-4.1421356237309504880168872420969394e-01
  2.41421356237309504880168872420969394]

julia> points = chebyshev_nodes(BigFloat,2,[3.0,-1.0])
[-0.4142135623730950488016887242096980785696718753769480731766797379907324784621193
  2.414213562373095048801688724209698078569671875376948073176679737990732478462119]
```
