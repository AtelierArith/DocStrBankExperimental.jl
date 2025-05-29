```
create_elem_restriction_strided(ceed::Ceed, nelem, elemsize, ncomp, lsize, strides)
```

Create a strided `CeedElemRestriction`.

!!! warning "Zero-based indexing"
    In the below notation, we are using **0-based indexing**. libCEED expects the offset indices to be 0-based.


# Arguments:

  * `ceed`:     The [`Ceed`](@ref) object
  * `nelem`:    Number of elements described by the restriction
  * `elemsize`: Size (number of "nodes") per element
  * `ncomp`:    Number of field components per interpolation node (1 for scalar fields)
  * `lsize`:    The size of the L-vector. This vector may be larger than the elements and             fields given by this restriction.
  * `strides`:  Array for strides between [nodes, components, elements]. Data for node $i$,             component $j$, element $k$ can be found in the L-vector at index `i*strides[0]             + j*strides[1] + k*strides[2]`. [`STRIDES_BACKEND`](@ref) may be used with             vectors created by a Ceed backend.
