```
calmax(x)
calmax!(x, val)
```

Specifies maximum element for display purposes. If not specified returns the maximum value in the collection.

## Examples

```jldoctest
julia> using FieldProperties

julia> x = reshape(1:16, 4, 4);

julia> calmax(x)
16

julia> struct ArrayMaxThresh{T,N}
           a::AbstractArray{T,N}
           calmax::T
       end

julia> calmax(ArrayMaxThresh(x, 10))
10
```
