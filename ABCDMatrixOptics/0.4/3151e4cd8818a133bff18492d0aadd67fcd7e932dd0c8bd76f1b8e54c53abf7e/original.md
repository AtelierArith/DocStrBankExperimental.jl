```
propagate(e::Union{Element, Vector{<:Element}}, b)
```

Propagate a beam `b` either by a single element `e::Element` or `Vector{<:Element}`.

Return is the final beam. Also available as `e * b`.

## Example

```jldoctest
julia> beam = FreeSpace(10) * GeometricBeam(w=10.0, k=1.0)
GeometricBeam{Float64}(20.0, 1.0, 10.0)

julia> beam = [ThinLens(10), FreeSpace(10)] * GeometricBeam(w=10.0, k=0.0)
GeometricBeam{Float64}(0.0, -1.0, 10.0)

julia> beam.w ≈ 0
true
```
