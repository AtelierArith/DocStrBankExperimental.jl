```
MetricBall(radii, rotation=I)
MetricBall(radius, metric=Euclidean())
```

A metric ball is a neighborhood that can be expressed in terms of a `metric` and a set of `radii`. The two main examples are the Euclidean ball an the Mahalanobis (ellipsoid) ball.

When multiple `radii` are provided, they can be rotated by a `rotation` specification from the [Rotations.jl](https://github.com/JuliaGeometry/Rotations.jl) package. Alternatively, a `metric` from the [Distances.jl](https://github.com/JuliaStats/Distances.jl) package can be specified together with a single `radius`.

## Examples

N-dimensional Euclidean ball with radius `1.0`:

```julia
julia> MetricBall(1.0)
```

Axis-aligned 3D ellipsoid with radii `(3.0, 2.0, 1.0)`:

```julia
julia> MetricBall((3.0, 2.0, 1.0))
```
