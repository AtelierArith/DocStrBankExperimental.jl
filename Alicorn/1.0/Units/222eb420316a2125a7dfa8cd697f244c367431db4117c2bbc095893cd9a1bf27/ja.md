```
convertToUnit(baseUnitExponents::BaseUnitExponents)
```

`BaseUnitExponents`オブジェクトに対応する`Unit`を返します。

# 例

```jldoctest
julia> jouleExponents = BaseUnitExponents(kg=1, m=2, s=-2)
BaseUnitExponents kg^1 m^2 s^-2 A^0 K^0 mol^0 cd^0

julia> convertToUnit(jouleExponents)
Unit kg m^2 s^-2
```
