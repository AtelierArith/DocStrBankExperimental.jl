```
struct MatDeforElastOrtho{
    MR<:AbstractDeforModelRed,
    FT,
    MTAN<:Function,
    MUPD<:Function,
    MTHS<:Function,
} <: AbstractMatDeforLinearElastic
```

線形直交弾性材料。
