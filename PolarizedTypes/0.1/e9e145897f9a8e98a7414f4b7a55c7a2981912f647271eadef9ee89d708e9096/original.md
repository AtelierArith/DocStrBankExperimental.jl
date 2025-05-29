```julia
struct PolBasis{B1<:Union{Missing, PolarizedTypes.ElectricFieldBasis}, B2<:Union{Missing, PolarizedTypes.ElectricFieldBasis}}
```

Denotes a general polarization basis, with basis vectors (B1,B2) which are typically `<: Union{ElectricFieldBasis, Missing}`
