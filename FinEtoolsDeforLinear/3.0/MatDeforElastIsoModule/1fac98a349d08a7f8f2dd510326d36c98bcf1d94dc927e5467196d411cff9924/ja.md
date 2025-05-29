```
struct MatDeforElastIso{
    MR<:AbstractDeforModelRed,
    FT,
    MTAN<:Function,
    MUPD<:Function,
    MTHS<:Function,
} <: AbstractMatDeforLinearElastic
```

線形等方性弾性材料。
