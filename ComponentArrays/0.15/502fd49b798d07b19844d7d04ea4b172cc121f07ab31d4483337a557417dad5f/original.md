```
getaxes(x::ComponentArray)
```

Access `.axes` field of a `ComponentArray`. This is different than `axes(x::ComponentArray)`, which     returns the axes of the contained array.

# Examples

```jldoctest
julia> using ComponentArrays

julia> ax = Axis(a=1:3, b=(4:6, (a=1, b=2:3)))
Axis(a = 1:3, b = (4:6, (a = 1, b = 2:3)))

julia> A = zeros(6,6);

julia> ca = ComponentArray(A, (ax, ax))
6×6 ComponentMatrix{Float64} with axes Axis(a = 1:3, b = (4:6, (a = 1, b = 2:3))) × Axis(a = 1:3, b = (4:6, (a = 1, b = 2:3)))
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

julia> getaxes(ca)
(Axis(a = 1:3, b = (4:6, (a = 1, b = 2:3))), Axis(a = 1:3, b = (4:6, (a = 1, b = 2:3))))
```
