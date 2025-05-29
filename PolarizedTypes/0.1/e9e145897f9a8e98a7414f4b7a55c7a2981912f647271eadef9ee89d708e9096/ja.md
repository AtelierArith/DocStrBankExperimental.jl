```julia
struct PolBasis{B1<:Union{Missing, PolarizedTypes.ElectricFieldBasis}, B2<:Union{Missing, PolarizedTypes.ElectricFieldBasis}}
```

一般的な偏光基底を示し、基底ベクトル (B1,B2) は通常 `<: Union{ElectricFieldBasis, Missing}` です。
