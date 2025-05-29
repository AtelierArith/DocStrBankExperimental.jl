```
ndims_space(x::PencilArray)
ndims_space(x::PencilArrayCollection)
```

Number of dimensions associated to the domain geometry.

These dimensions correspond to the leftmost indices of the array.

The total number of dimensions of a `PencilArray` is given by:

```
ndims(x) == ndims_space(x) + ndims_extra(x)
```
