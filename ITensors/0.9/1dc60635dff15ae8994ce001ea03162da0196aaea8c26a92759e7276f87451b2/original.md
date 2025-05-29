```
ITensor([::Type{ElT} = Float64,] ::UndefInitializer, flux::QN, inds)
ITensor([::Type{ElT} = Float64,] ::UndefInitializer, flux::QN, inds::Index...)
```

Construct an ITensor with indices `inds` and BlockSparse storage with undefined elements of type `ElT`, where the nonzero (allocated) blocks are determined by the provided QN `flux`. One purpose for using this constructor is that initializing the elements in an undefined way is faster than initializing them to a set value such as zero.

The storage will have `NDTensors.BlockSparse` type.

# Examples

```julia
i = Index([QN(0)=>1, QN(1)=>2], "i")
A = ITensor(undef,QN(0),i',dag(i))
B = ITensor(Float64,undef,QN(0),i',dag(i))
C = ITensor(ComplexF64,undef,QN(0),i',dag(i))
```
