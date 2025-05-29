```
Nilp(vector::AbstractVector, size::Ti) where {Ti<:Integer}
```

Create a nilpotent matrix whose dimension is `size` from user-provided vector. The non-zero diagonal of nilpotent matrix is fixed as the one with offset `1`. Therefore, the size of given `vector` should at least be `size-1`.

## Examples

```jldoctest; setup = :(using SMG2S)
julia> vec=[1; 1; 0; 1; 1; 1; 0]
7-element Vector{Int64}:
 1
 1
 0
 1
 1
 1
 0

julia> SMG2S.Nilp(vec, 8)
Nilpotent{Int64}(3, 8, 4,
  ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅ )
```
