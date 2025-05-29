```
MetricSystem(Mu=Mᵤ,μ0=μ₀,Ru=Rᵤ,g0=𝟏,θ=𝟏,h=𝘩,me=R∞*𝟐*h/𝘤/α^2)
```

`molarmass` 定数、`vacuumpermeability`、`molargas` 定数、`gravity` 力の基準、`angle` スケール、および `planck` 定数から新しい `UnitSystem` を構築します。

```Julia
UnitSystem(Ru*me/Mu/μₑᵤ/g0,h/τ/g0/θ,𝘤,μ0,me,Mu,Kcd*(mₑ/me)^2*(h/𝘩)*g0,θ,𝟏,𝟏,g0)
```

例には `SI2019`、`SI1976`、`Metric`、`Engineering`、`MetricTurn`、`MetricSpatian`、`MetricGradian`、`MetricDegree`、`MetricArcminute`、`MetricArcsecond` が含まれます。さらに、`ConventionalSystem` コンストラクタは `MetricSystem` を基にしており、バリエーションを生成します。

`British` や `English`、`IAU` などの他の派生 `UnitSystem` インスタンスは、`MetricSystem` によって生成された既存の `Metric` 仕様から派生しています。コンストラクタ `MetricSystem` は、いくつかの標準的な共通数値を組み込み、カスタマイズのために置き換え可能な可変引数を公開し、共通の `Universe` を持つ歴史的なバリエーションを生成する能力を持っています。派生コンストラクタには `EntropySystem`、`ElectricSystem`、`GaussSystem`、`RankineSystem`、および `AstronomicalSystem` があります。
