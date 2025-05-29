```
ITensor([ElT::Type, ]x::Number, flux::QN, inds)
ITensor([ElT::Type, ]x::Number, flux::QN, inds::Index...)
```

Construct an ITensor with all elements consistent with QN flux `flux` set to `x` and indices `inds`.

If `x isa Int` or `x isa Complex{Int}` then the elements will be set to `float(x)` unless specified otherwise by the first input.

The storage will have `NDTensors.BlockSparse` type.

# Examples

```julia
i = Index([QN(0)=>1, QN(1)=>2], "i")
A = ITensor(2.3, QN(0), i', dag(i))
B = ITensor(Float64, 3.5, QN(0), i', dag(i))
C = ITensor(ComplexF64, 4, QN(0), i', dag(i))
```

!!! warning
    In future versions this may not automatically convert integer inputs with `float`, and in that case the particular element type should not be relied on.

