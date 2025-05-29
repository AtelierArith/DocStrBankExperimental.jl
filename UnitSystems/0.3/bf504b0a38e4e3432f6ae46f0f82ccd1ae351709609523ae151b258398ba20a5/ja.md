```Julia
mpge(U::UnitSystem) = mile(U)/gasgallon(U)
```

長さあたりのエネルギー（N⁻¹またはlb⁻¹）の`mile`あたりの`gasgallon`の同等の参照単位。

```Julia
julia> mpge(Metric) # N⁻¹
1.3380584481180183e-5

julia> mpge(CGS) # dyn⁻¹
1.3380584481180183e-10

julia> mpge(English) # lb⁻¹
5.95198051140049e-5
```
