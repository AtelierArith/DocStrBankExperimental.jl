```
enthalpy_vap(model::EoSModel, T,method = ChemPotVSaturation(x0_sat_pure(model,T)))
```

温度 `T` における飽和蒸気と液体のエンタルピーの差 `ΔH` を J で計算します。
