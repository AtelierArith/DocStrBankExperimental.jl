```
CeedVector(c::Ceed, len::Integer; allocate::Bool=true)
```

Creates a `CeedVector` of given length. If `allocate` is false, then no memory is allocated. Attemping to access the vector before calling `setarray!` will fail. By default, `allocate` is true, and libCEED will allocate (host) memory for the vector.
