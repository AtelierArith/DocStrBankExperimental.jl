SeaWaterDensity(Θ,Σ,Π,Π0)

潜在密度 (ρP)、現場密度 (ρI)、および PREF (Π0, デカバール単位) に基づく密度を、潜在温度 (Θ, °C 単位)、塩分 (Σ, psu 単位)、および圧力 (Π, デカバール単位) から計算します。これは、UNESCO / Jackett & McDougall 1994 の状態方程式に従います。

クレジット: コードは B. Ferron による Matlab 実装に基づいています。参考文献: https://www.jodc.go.jp/info/ioc*doc/UNESCO*tech/059832eb.pdf チェック値: ρI = `1041.83267kg/m^3` で Θ=`3°Celcius`、Σ=`35psu`、Π=`3000dbar`

```
(ρP,ρI,ρR) = SeaWaterDensity(3.,35.5,3000.)
isapprox(ρI,1041.83267, rtol=1e-6)
```
