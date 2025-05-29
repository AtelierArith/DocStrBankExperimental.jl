```
FEMMDeforLinearIMH8(
    mr::Type{MR},
    integdomain::ID,
    material::M,
    nmodes::Int64,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function}, M<:AbstractMatDeforLinearElastic}
```

コンストラクタで、互換性のないモードの数をオプションで設定できます。
