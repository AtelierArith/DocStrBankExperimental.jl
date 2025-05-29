```
osmotic_coefficient_sat(model::ESElectrolyteModel,salts,T,m,zsolvent=[1.])
```

特定の温度とモラリティでの飽和点における溶媒の浸透圧係数を計算します。これらは次のように定義されます：

```
ϕ = -1/(∑νi*mi*Mw)*log(asolv)
```

例：

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

T = 298.15
m = [1.0]

ϕ = osmotic_coefficient(model,salts,T,m)
```

複数の溶媒が存在する場合、溶媒の組成は`zsolvent`キーワード引数で指定できます。
