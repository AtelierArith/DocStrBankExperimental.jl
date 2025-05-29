```
Batch{A, M <: AnalysisMethod{A}, C <: AbstractVector{<: AbstractCalibration{<: A}}, D <: Union{AnalysisTable{<: A}, Nothing}}
```

定量分析のためのバッチを表す型です。`A` は分析物のタイプを決定し、`T` はテーブルのタイプを決定します。

# フィールド

  * `method`: `M`、メソッド。
  * `calibration`: `C`、キャリブレーション曲線。
  * `data`: `D`、分析のためのデータ。

# プロパティ

  * `analyte`: `AbstractVector{A}`、ユーザー定義型の分析物、`method.analyte` と同じ。
  * `isd`: `AbstractVector{<: A}`、内部標準である分析物、`method.isd` と同じ。
  * `nonisd`: `AbstractVector{<: A}`、内部標準でない分析物、`method.nonisd` と同じ。
  * `point`: `AbstractVector` または `Nothing`、キャリブレーションポイント、`method.point` と同じ。
  * `level`: `AbstractVector{Int}`、キャリブレーションレベル、`method.level` と同じ。

# コンストラクタ

  * `Batch(method, calibration, data = nothing)`
