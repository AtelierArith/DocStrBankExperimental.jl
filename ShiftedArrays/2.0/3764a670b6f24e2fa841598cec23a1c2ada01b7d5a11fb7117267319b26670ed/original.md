```
CircShiftedArray(parent::AbstractArray, shifts)
```

Custom `AbstractArray` object to store an `AbstractArray` `parent` circularly shifted by `shifts` steps (where `shifts` is a `Tuple` with one `shift` value per dimension of `parent`). Use `copy` to collect the values of a `CircShiftedArray` into a normal `Array`.

!!! note
    `shift` is modified with a modulo operation and does not store the passed value but instead a nonnegative number which leads to an equivalent shift.


!!! note
    If `parent` is itself a `CircShiftedArray`, the constructor does not nest `CircShiftedArray` objects but rather combines the shifts additively.


# Examples

```jldoctest circshiftedarray
julia> v = [1, 3, 5, 4];

julia> s = CircShiftedArray(v, (1,))
4-element CircShiftedVector{Int64, Vector{Int64}}:
 4
 1
 3
 5

julia> copy(s)
4-element Vector{Int64}:
 4
 1
 3
 5
```
