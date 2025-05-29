```
trace(elems::Vector{<:Element}, b0::AbstractBeam)
```

Trace a beam `b0` through a vector of elements `elems`. All intermediate states of the beam will be recorded.

Return is a `Vector` of states where the last entry is the final beam. Final beam is equivalent to `propagate(elems, b0)`.

## Example

```jldoctest
julia> trace([ThinLens(10), FreeSpace(10)], GeometricBeam(w=10.0, k=0.0))
3-element Vector{GeometricBeam{Float64}}:
 GeometricBeam{Float64}(10.0, 0.0, 0.0)
 GeometricBeam{Float64}(10.0, -1.0, 0.0)
 GeometricBeam{Float64}(0.0, -1.0, 10.0)
```
