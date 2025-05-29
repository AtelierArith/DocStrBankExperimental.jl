```
ndims_extra(::Type{<:PencilArray})
ndims_extra(x::PencilArray)
ndims_extra(x::PencilArrayCollection)
```

Number of "extra" dimensions associated to `PencilArray`.

These are the dimensions that are not associated to the domain geometry. For instance, they may correspond to vector or tensor components.

These dimensions correspond to the rightmost indices of the array.

The total number of dimensions of a `PencilArray` is given by:

```
ndims(x) == ndims_space(x) + ndims_extra(x)
```
