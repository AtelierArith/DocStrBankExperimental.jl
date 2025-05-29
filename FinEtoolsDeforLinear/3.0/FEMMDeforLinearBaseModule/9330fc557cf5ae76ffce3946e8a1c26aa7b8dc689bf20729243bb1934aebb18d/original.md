```
thermalstrainloads(
    self::AbstractFEMMDeforLinear,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
) where {A<:AbstractSysvecAssembler,GFT<:Number,UFT<:Number,TFT<:Number}
```

Compute the thermal-strain load vector.
