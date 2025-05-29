```
ITensor([::Type{ElT} = Float64, ]inds)
ITensor([::Type{ElT} = Float64, ]inds::Index...)
```

Construct an ITensor filled with zeros having indices `inds` and element type `ElT`. If the element type is not specified, it defaults to `Float64`.

The storage will have `NDTensors.Dense` type.

# Examples

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = ITensor(i,j)
B = ITensor(ComplexF64,k,j)
```
