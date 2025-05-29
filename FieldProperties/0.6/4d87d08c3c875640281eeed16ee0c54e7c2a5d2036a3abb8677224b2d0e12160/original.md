```
calmin(x)
calmin!(x, val)
```

Specifies minimum element for display purposes. If not specified returns the minimum value in the collection.

## Examples

```jldoctest
julia> using FieldProperties

julia> x = reshape(1:16, 4, 4);

julia> calmin(x)
1

julia> struct ArrayMinThresh{T,N}
           a::AbstractArray{T,N}
           calmin::T
       end

julia> calmin(ArrayMinThresh(x, 5))
5
```
