```Julia
horsepower(U::UnitSystem) = power(𝟐*𝟓^2*𝟏𝟏,U,British)
```

`power`の単位は、1秒間に1フィートを1ポンドで持ち上げることから導出されます。

```Julia
julia> horsepower(British) # lb⋅ft⋅s⁻¹
550

julia> horsepower(Metric) # W
745.6998715822704

julia> horsepower(Engineering) # kgf⋅m⋅s⁻¹
76.04022490680002
```
