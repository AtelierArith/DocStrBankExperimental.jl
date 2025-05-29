```
osmotic_coefficient(model::ESElectrolyteModel,salts,p,T,m,zsolvent=[1.])
```

与圧力、温度、モラル濃度における溶媒の浸透圧係数を計算します。これらは次のように定義されます：

```
ϕ = -1/(∑νi*mi*Mw)*log(asolv)
```

例：

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

p = 1e5
T = 298.15
m = [1.0]

ϕ = osmotic_coefficient(model,salts,p,T,m)
```

複数の溶媒が存在する場合、溶媒の組成は`zsolvent`キーワード引数で指定できます。
