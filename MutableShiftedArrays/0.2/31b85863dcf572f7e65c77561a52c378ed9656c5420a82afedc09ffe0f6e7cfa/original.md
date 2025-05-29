```
MutableShiftedArray(parent::AbstractArray, shifts = (), viewsize=size(v); default = zero(eltype(parent)))
```

Custom `AbstractArray` object to store an `AbstractArray` `parent` shifted by `shifts` steps (where `shifts` is a `Tuple` with one `shift` value per dimension of `parent`). As opposed to `ShiftedArray` of the `ShiftedArrays.jl` toolbox, this object is mutable and mutation operations in the padded ranges are ignored. Furthermore it also supports size changes in the view.

For `s::MutableShiftedArray`, `s[i...] == s.parent[map(-, i, s.shifts)...]` if `map(-, i, s.shifts)` is a valid index for `s.parent`, and `s.v[i, ...] == default` otherwise. Use `copy` to collect the values of a `MutableShiftedArray` into a normal `Array`. The recommended constructor is `MutableShiftedArray(parent, shifts; default = missing)`.

!!! note
    If `parent` is itself a `MutableShiftedArray` with a compatible default value, the constructor does not nest `MutableShiftedArray` objects but rather combines the shifts additively.


# Arguments

  * `parent::AbstractArray`: the array to be shifted
  * `shifts::Tuple{Int}`: the amount by which `parent` is shifted in each dimension. The default, an empty Tuple will result in no shifts.
  * `viewsize::Tuple{Int}`: the size of the view. By default the size of the parent array is used.
  * `default::M`: the default value to return when out of bounds in the original array. By default zero of the corresponding `eltype` is used.               Note that using `missing` as default value will cause single index accesses in CUDA due to the Union type.

# Examples

```jldoctest shiftedarray
julia> v = [1, 3, 5, 4];

julia> s = MutableShiftedArray(v, (1,))
4-element MutableShiftedVector{Int64, Int64, Vector{Int64}}:
 0
 1
 3
 5

julia> copy(s)
4-element Vector{Int64}:
 0
 1
 3
 5

julia> v = reshape(1:16, 4, 4);

julia> s = MutableShiftedArray(v, (0, 2), default=missing)
4×4 MutableShiftedArray{Int64, Missing, 2, Base.ReshapedArray{Int64, 2, UnitRange{Int64}, Tuple{}}}:
 missing  missing  1  5
 missing  missing  2  6
 missing  missing  3  7
 missing  missing  4  8

julia> shifts(s)
(0, 2)
```
