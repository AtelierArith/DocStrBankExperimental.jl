```
mean_ionic_activity_coefficient_sat(model::ESElectrolyteModel,salts,T,m,zsolvent=[1.])
```

特定の温度とモラリティでの飽和点における塩の選択の平均イオン活性係数を計算します。これらは次のように定義されます：

```
γ± = φ±/φ±₀ * ∑zsolv/∑z
```

例：

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

T = 298.15
m = [1.0]

γ± = mean_ionic_activity_coefficient_sat(model,salts,T,m)
```

複数の溶媒が存在する場合、溶媒の組成は`zsolvent`キーワード引数で指定できます。
