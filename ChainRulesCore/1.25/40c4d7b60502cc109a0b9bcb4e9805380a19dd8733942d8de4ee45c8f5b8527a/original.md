```
ProjectTo(x)
```

Returns a `ProjectTo{T}` functor which projects a tangent `dx` onto the relevant tangent space for `x`.

Custom `ProjectTo` methods are provided for many subtypes of `Number` (to e.g. ensure precision), and `AbstractArray` (to e.g. ensure sparsity structure is maintained by tangent). Called on unknown types it will (as of v1.5.0) simply return `identity`, thus can be safely applied to arbitrary `rrule` arguments.

# Examples

```jldoctest
julia> pr = ProjectTo(1.5f0)  # preserves real numbers, and floating point precision
ProjectTo{Float32}()

julia> pr(3 + 4im)
3.0f0

julia> pd = ProjectTo(Diagonal([1,2,3]))  # preserves structured matrices
ProjectTo{Diagonal}(diag = ProjectTo{AbstractArray}(element = ProjectTo{Float64}(), axes = (Base.OneTo(3),)),)

julia> th = @thunk reshape(1:9,3,3);

julia> pd(th) isa Thunk
true

julia> unthunk(pd(th))
3×3 Diagonal{Float64, Vector{Float64}}:
 1.0   ⋅    ⋅
  ⋅   5.0   ⋅
  ⋅    ⋅   9.0

julia> ProjectTo([1 2; 3 4]')  # no special structure, integers are promoted to float(x)
ProjectTo{AbstractArray}(element = ProjectTo{Float64}(), axes = (Base.OneTo(2), Base.OneTo(2)))
```
