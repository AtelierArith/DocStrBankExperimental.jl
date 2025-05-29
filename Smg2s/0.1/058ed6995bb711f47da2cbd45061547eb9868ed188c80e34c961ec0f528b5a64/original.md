```
Nilp(vec::AbstractVector, diag::Ti, size::Ti) where{Ti <: Integer}
```

Create a nilpotent matrix whose dimension is `size` from user-provided vector. The non-zero diagonal of nilpotent matrix is set as the one with offset `diag`. Therefore, the size of given `vector` should at least be `size-diag`.

## Examples

```jldoctest; setup = :(using SMG2S; using SparseArrays)
julia> vec=[1; 1; 0; 1; 1; 1; 0]
7-element Vector{Int64}:
 1
 1
 0
 1
 1
 1
 0

julia> SMG2S.Nilp(vec, 3, 8)
┌ Info: the degree of given nilpotent matrix is:
└   degree = 3
Nilpotent{Int64}(1, 8, 3,
 ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅)

```
