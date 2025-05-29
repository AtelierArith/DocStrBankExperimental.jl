```
ITensor([::Type{ElT} = Float64, ]::UndefInitializer, inds)
ITensor([::Type{ElT} = Float64, ]::UndefInitializer, inds::Index...)
```

Construct an ITensor filled with undefined elements having indices `inds` and element type `ElT`. If the element type is not specified, it defaults to `Float64`. One purpose for using this constructor is that initializing the elements in an   undefined way is faster than initializing them to a set value such as zero.

The storage will have `NDTensors.Dense` type.

# Examples

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = ITensor(undef,i,j)
B = ITensor(ComplexF64,undef,k,j)
```
