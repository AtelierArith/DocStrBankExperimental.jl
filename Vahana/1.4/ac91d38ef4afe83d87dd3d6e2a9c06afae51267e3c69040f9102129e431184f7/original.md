```
create_namedtuple_converter(T::DataType)
```

The HDF5.jl library does not support the storage of nested structs, but structs can have `NamedTuples` as fields. This function creates a convert function from a struct to a corresponding `NamedTuple` (and also the other way around), so after calling this for a type `T`, `T` can be the type of an agent/edge/param/global field.
