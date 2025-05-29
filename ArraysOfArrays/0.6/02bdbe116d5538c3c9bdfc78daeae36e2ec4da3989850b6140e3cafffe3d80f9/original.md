```
abstract_nestedarray_type(T_inner::Type, ::Val{ndims_tuple})
```

Return the type of nested `AbstractArray`s. `T_inner` specifies the element type of the innermost layer of arrays, `ndims_tuple` specifies the dimensionality of each nesting layer (outer arrays first).

If `ndims_tuple` is empty, the returns is the (typically scalar) type `T_inner` itself.
