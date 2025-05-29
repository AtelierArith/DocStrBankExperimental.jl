```
create_elem_restriction(
    ceed::Ceed,
    nelem,
    elemsize,
    ncomp,
    compstride,
    lsize,
    offsets::AbstractArray{CeedInt},
    mtype::MemType=MEM_HOST,
    cmode::CopyMode=COPY_VALUES,
)
```

Create a `CeedElemRestriction`.

!!! warning "Zero-based indexing"
    In the below notation, we are using **0-based indexing**. libCEED expects the offset indices to be 0-based.


# Arguments:

  * `ceed`:       The [`Ceed`](@ref) object
  * `nelem`:      Number of elements described in the `offsets` array
  * `elemsize`:   Size (number of "nodes") per element
  * `ncomp`:      Number of field components per interpolation node (1 for scalar fields)
  * `compstride`: Stride between components for the same L-vector "node". Data for node $i$,               component $j$, element $k$ can be found in the L-vector at index `offsets[i               + k*elemsize] + j*compstride`.
  * `lsize`:      The size of the L-vector. This vector may be larger than the elements and               fields given by this restriction.
  * `offsets`:    Array of shape `(elemsize, nelem)`. Column $i$ holds the ordered list of the               offsets (into the input [`CeedVector`](@ref)) for the unknowns corresponding               to element $i$, where $0 \leq i < \textit{nelem}$. All offsets must be in               the range $[0, \textit{lsize} - 1]$.
  * `mtype`:      Memory type of the `offsets` array, see [`MemType`](@ref)
  * `cmode`:      Copy mode for the `offsets` array, see [`CopyMode`](@ref)
