```julia
struct FullFactorial <: ExperimentalDesign.AbstractFactorialDesign
```

*明示的* フルファクタリアルデザインをカプセル化し、すべての実験が完全に計算され、保存されます。 [`IterableFullFactorial`](@ref) を使用して、フルファクタリアルデザインの要素に任意にアクセスできる *暗黙的* ファクタリアルデザインを取得します。

  * `matrix::DataFrames.DataFrame`
  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`
