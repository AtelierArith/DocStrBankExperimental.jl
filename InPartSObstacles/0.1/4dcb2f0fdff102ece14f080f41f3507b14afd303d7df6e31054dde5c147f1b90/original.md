```
InfiniteWall{N, OT <: ObstacleType}(support::SVector{N, Float64}, normal::SVector{N, Float64})
```

Infinite wall obstacle type with arbitrary normal vector. The normal vector points out of the wall and it must be normalized to unit length. Type parameter `N` refers the dimension of the system, `OT` is the obstacle type, which can be either `Absorbing` or `Reflecting`.

Constructors:

```
InfiniteWall(support::AbstractVector, φ::Float64)
```

where φ gives the direction of the wall normal in radians.

```
makewall(T::Type{<:InfiniteWall{2}}, p1::SVector{2, Float64}, p2::SVector{2, Float64})=
makewall(T::Type{<:InfiniteWall{3}}, p1::SVector{3, Float64}, p2::SVector{3, Float64}, p3::SVector{3, Float64}) =
```

for constructing walls from two or three points.

A default implementation for particle interaction is provided for `Absorbing` walls. Interactions with reflecting walls can be added by defining:

```julia
    function InPartS.obstacleforces!(so::InfiniteWall{DIMENSION, Reflecting}, p::YourParticleType, sim::Simulation)
        # ...
    end
```
