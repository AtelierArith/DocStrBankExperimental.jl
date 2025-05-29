```
FitOptions
```

フィッティングを制御するための構造体。

## フィールド

  * `what_fit::Dict{AbstractTransportProperty,Vector{Bool}}`: フィットするパラメータを指定する

## 例

```
FitOptions(;
    what_fit=Dict(
        ThermalConductivity()=>ones(Bool,5), 
        SelfDiffusionCoefficient()=>Bool[0,0,0,1,1])
)
```
