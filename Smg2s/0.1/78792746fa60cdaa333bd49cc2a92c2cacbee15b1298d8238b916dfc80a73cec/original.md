```
Nilp(nbOne::Ti, size::Ti) where {Ti<:Integer}
```

Create a nilpotent matrix object with parameters `nbOne` and `size`. `size` refers to the size of nilpotent matrix to be generated, and `nbOne` refers to the number of continuous `1` on the non-zero diagonal of generated nilptent matrix.

This is the default type of nilptent matrix used by SMG2S, in which the non-zero diagonal is selected as the one of offset `1`. This diagonal starts with `nbOne` number of `1`, then a `0`, then `nbOne` number of `1`, ... until to the end.

## Examples

```jldoctest; setup = :(using SMG2S)
julia> SMG2S.Nilp(2,8)
Nilpotent{Int64}(2, 8, 3,
  ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅   1.0   ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0   ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅ )
```
