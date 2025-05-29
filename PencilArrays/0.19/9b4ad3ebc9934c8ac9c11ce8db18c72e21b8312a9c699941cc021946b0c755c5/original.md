```
ManyPencilArray{T,N,M} <: AbstractManyPencilArray{N,M}
```

Container holding `M` different [`PencilArray`](@ref) views to the same underlying data buffer. All views share the same element type `T` and dimensionality `N`.

This can be used to perform in-place data transpositions with [`transpose!`](@ref Transpositions.transpose!).

---

```
ManyPencilArray{T}(undef, pencils...; extra_dims=())
```

Create a `ManyPencilArray` container that can hold data of type `T` associated to all the given [`Pencil`](@ref)s.

The optional `extra_dims` argument is the same as for [`PencilArray`](@ref).
