```
stiffness(
    self::FEMM,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {FEMM<:AbstractFEMMDeforLinear,A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

剛性行列を計算して組み立てます。

!!! note "均質材料のみ"
    材料の剛性行列は、領域のすべての点で同じであると仮定されています（均質材料）。

