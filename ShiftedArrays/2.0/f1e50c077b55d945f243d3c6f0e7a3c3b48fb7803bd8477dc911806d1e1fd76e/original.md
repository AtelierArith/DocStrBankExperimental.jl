```
ShiftedArray(parent::AbstractArray, shifts, default)
```

Custom `AbstractArray` object to store an `AbstractArray` `parent` shifted by `shifts` steps (where `shifts` is a `Tuple` with one `shift` value per dimension of `parent`). For `s::ShiftedArray`, `s[i...] == s.parent[map(-, i, s.shifts)...]` if `map(-, i, s.shifts)` is a valid index for `s.parent`, and `s.v[i, ...] == default` otherwise. Use `copy` to collect the values of a `ShiftedArray` into a normal `Array`. The recommended constructor is `ShiftedArray(parent, shifts; default = missing)`.

!!! note
    If `parent` is itself a `ShiftedArray` with a compatible default value, the constructor does not nest `ShiftedArray` objects but rather combines the shifts additively.


# Examples

```jldoctest shiftedarray
julia> v = [1, 3, 5, 4];

julia> s = ShiftedArray(v, (1,))
4-element ShiftedVector{Int64, Missing, Vector{Int64}}:
  missing
 1
 3
 5

julia> v = [1, 3, 5, 4];

julia> s = ShiftedArray(v, (1,))
4-element ShiftedVector{Int64, Missing, Vector{Int64}}:
  missing
 1
 3
 5

julia> copy(s)
4-element Vector{Union{Missing, Int64}}:
  missing
 1
 3
 5

julia> v = reshape(1:16, 4, 4);

julia> s = ShiftedArray(v, (0, 2))
4×4 ShiftedArray{Int64, Missing, 2, Base.ReshapedArray{Int64, 2, UnitRange{Int64}, Tuple{}}}:
 missing  missing  1  5
 missing  missing  2  6
 missing  missing  3  7
 missing  missing  4  8

julia> shifts(s)
(0, 2)
```
