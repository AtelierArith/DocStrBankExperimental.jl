```
SpreadingRateTemp(Tsurface=0, Tmantle=1350, Adiabat=0, MORside="left",SpreadingVel=3, AgeRidge=0, maxAge=80)
```

ボックス内に半空間温度構造を設定し、プレートの年齢が変化することを示す拡散速度を組み合わせます。

# パラメータ

  * Tsurface : 表面温度 [C]
  * Tmantle : マントル温度 [C]
  * Adiabat : マントルアディアバット [K/km]
  * MORside : MORが位置するボックスの側 ["left","right","front","back"]
  * SpreadingVel : 拡散速度 [cm/yr]
  * AgeRidge : リッジの熱年齢 [Myrs]
  * maxAge : プレートの最大熱年齢 [Myrs]

注意: 中央海嶺での熱年齢はゼロ除算を避けるために1年に設定されています。
