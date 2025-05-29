```
empty_sparse_vector!(
    fill::Function,
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal},
    nnz::StorageInteger,
    indtype::Maybe{Type{<:StorageInteger}} = nothing;
    [overwrite::Bool = false]
)::Any
```

Create an empty sparse vector property with some `name` for some `axis` in `daf`, pass its parts (`nzind` and `nzval`) to `fill`, and return the result.

If `indtype` is not specified, it is chosen automatically to be the smallest unsigned integer type needed for the vector.

The returned vector will be uninitialized; the caller is expected to `fill` its `nzind` and `nzval` vectors with values. Specifying the `nnz` makes their sizes known in advance, to allow pre-allocating disk data. For this reason, this does not work for strings, as they do not have a fixed size.

This severely restricts the usefulness of this function, because typically `nnz` is only know after fully computing the matrix. Still, in some cases a large sparse vector is created by concatenating several smaller ones; this function allows doing so directly into the data vector, avoiding a copy in case of memory-mapped disk formats.

!!! warning
    It is the caller's responsibility to fill the two vectors with valid data. Specifically, you must ensure:

      * `nzind[1] == 1`
      * `nzind[i] <= nzind[i + 1]`
      * `nzind[end] == nnz`


This first verifies the `axis` exists in `daf` and that the property name isn't `name`. If not `overwrite` (the default), this also verifies the `name` vector does not exist for the `axis`.
