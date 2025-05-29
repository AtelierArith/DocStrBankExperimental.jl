```
EntropySystem(U::UnitSystem,t,l,m,θ=𝟏)
EntropySystem(U::UnitSystem,t,l,m,θ,μ0,Mu=molarmass(U)/m,g0=gravity(U))
```

新しい `UnitSystem` を `U` から、最初の4つのパラメータによって `time`、`length`、`mass`、および `temperature` に沿ってスケール変更して構築します。追加のオプションパラメータにより、`vacuumpermeability`、`molarmass`、および `gravity` 定数のカスタマイズが可能です。

このタイプの例には `Nautical`、`Meridian`、`Gravitational`、`MTS`、`KKH`、`MPH`、`IAU☉`、`IAUE`、`IAUJ`、`Hubble`、`Cosmological`、`CosmologicalQuantum` が含まれます。しかし、`UnitSystem` の派生のためのほとんどの他のコンストラクタは、`EntropySystem` を内部的に呼び出すことに基づいています。例えば `AstronomicalSystem`、`ElectricSystem`、`GaussSystem`、および `RankineSystem` です。これは、`EntropySystem` がそこにリストされている例も構築することを意味します。
