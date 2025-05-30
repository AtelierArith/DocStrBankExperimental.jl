```
struct MatDeforElastOrtho{
    MR<:AbstractDeforModelRed,
    FT,
    MTAN<:Function,
    MUPD<:Function,
    MTHS<:Function,
} <: AbstractMatDeforLinearElastic
```

線形異方性弾性材料。
