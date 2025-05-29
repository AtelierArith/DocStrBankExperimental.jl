```
mean_ionic_activity_coefficient(model::ESElectrolyteModel,salts,p,T,m,zsolvent=[1.])
```

塩の選択における平均イオン活動係数を、特定の圧力、温度、モラリティで計算します。これらは次のように定義されます：

```
γ± = φ±/φ±₀ * ∑zsolv/∑z
```

例：

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

p = 1e5
T = 298.15
m = [1.0]

γ± = mean_ionic_activity_coefficient(model,salts,p,T,m)
```

複数の溶媒が存在する場合、溶媒の組成は `zsolvent` キーワード引数で指定できます。
