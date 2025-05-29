```
Interval{T} <: AbstractRayInterval{T}
```

Datatype representing an interval between two [`IntervalPoint`](@ref)s on a ray.

The lower element can either be [`RayOrigin`](@ref) or an [`Intersection`](@ref). The upper element can either be an [`Intersection`](@ref) or [`Infinity`](@ref).

```julia
positivehalfspace(int::Intersection) -> Interval with lower = int, upper = Infinity
rayorigininterval(int::Intersection) -> Interval with lower = RayOrigin, upper = int
Interval(low, high)
```

Has the following accessor methods:

```julia
lower(a::Interval{T}) -> Union{RayOrigin{T},Intersection{T,3}}
upper(a::Interval{T}) -> Union{Intersection{T,3},Infinity{T}}
```
