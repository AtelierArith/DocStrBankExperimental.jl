```
ClapeyronSaturation <: SaturationMethod
ClapeyronSaturation(T0 = nothing, crit = nothing, satmethod = ChemPotVSaturation())
```

`saturation_temperature`のための飽和法。Clapeyron方程式を使用して、収束するまで`saturation_temperature(model, Ti, satmethod)`を反復的に解決します：

```
dp/dT = ΔS/ΔV
```

それは臨界点（または提供された場合は`T0`）から降下します。信頼性がありますが、遅いです。

`T0 > Tsat`であることをお勧めします。温度減少の反復系列はより安定しています。Clapeyron 0.3.7までの`saturation_temperature`のデフォルトの方法です。
