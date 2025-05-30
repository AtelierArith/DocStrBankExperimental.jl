SeaWaterDensity(Θ,Σ,Π,Π0)

潜在密度 (ρP)、現場密度 (ρI)、および PREF に基づく密度 (Π0 はデカバール) を、潜在温度 (Θ は °C)、塩分 (Σ は psu)、および圧力 (Π はデカバール) に基づいて、UNESCO / Jackett & McDougall 1994 の状態方程式に従って計算します。

クレジット: コードは B. Ferron による Matlab 実装に基づいています 参考文献: https://www.jodc.go.jp/info/ioc*doc/UNESCO*tech/059832eb.pdf チェック値: ρI = `1041.83267kg/m^3` で Θ=`3°Celcius`、Σ=`35psu`、Π=`3000dbar`

```
(ρP,ρI,ρR) = SeaWaterDensity(3.,35.5,3000.)
isapprox(ρI,1041.83267, rtol=1e-6)
```
