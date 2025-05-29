Computes `N` points of type `T` according to `node_generator` and scales the points to the interval given in `domain` (defaults to [1.0,-1.0]).  Return the points in a struct (ChebRoots, ChebExtrema,  ChebExtended) according to the `node_generator`.

# Signature

points = nodes(T,N,node_generator,domain)

# Examples

```
julia> using DoubleFloats
julia> points = nodes(Double64,4,:chebyshev_nodes)
julia> points = nodes(Double64,4,:chebyshev_extrema)
julia> points = nodes(Double64,4,:chebyshev_extended)

julia> points = nodes(Double64,4,:chebyshev_nodes,[3.0,-1.0])
julia> points = nodes(Double64,4,:chebyshev_extrema,[3.0,-1.0])
julia> points = nodes(Double64,4,:chebyshev_extended,[3.0,-1.0])
```
