```julia
struct PlackettBurman <: ExperimentalDesign.AbstractScreeningDesign
```

Paleyの方法を使用して構築されたPlackett-Burmanスクリーニングデザインをカプセル化します。因子レベルは`:high`および`:low`シンボルとしてエンコードされ、因子間の相互作用をエイリアスする可能性のある追加のダミー変数がデザインをパディングするために追加されます。

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `dummy_factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
