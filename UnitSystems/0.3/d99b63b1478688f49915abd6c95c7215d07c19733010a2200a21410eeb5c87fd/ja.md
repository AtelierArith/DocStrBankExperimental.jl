```
ElectricSystem(U::UnitSystem,Ω,V) = EntropySystem(U,𝟏,𝟏,V^2/Ω,𝟏,vacuumpermeability(U)/Ω)
```

`U`から`UnitSystem`を新たに構築し、`mass`を`electricpotential`と`resistance`で再スケールします。`International`システムでは、`Ωᵢₜ`と`Vᵢₜ`は最近のアメリカの結果からの定義として使用され、一方で`InternationalMean`では他の国に基づく以前の推定値が使用されました。
