```
AnalysisMethod{A, M <: Table, C <: AbstractDataTable, D <: Union{AbstractDataTable, Nothing}}
```

分析方法を含む型で、分析物の設定とソースキャリブレーションデータを含みます。`A`は分析物のタイプを決定します。

# フィールド

  * `analytetable`: `M`は3つの列を含みます。

      * `analyte`: `AbstractVector{A}`、ユーザー定義型の分析物。
      * `isd`: `AbstractVector{Int}`、内部標準のインデックス。`0`は内部標準がないことを意味し、`-1`は分析物自体が内部標準であることを意味します。
      * `calibration`: キャリブレーション曲線のための分析物のインデックス。`-1`は分析物自体が内部標準であることを意味し、したがってキャリブレーション曲線には含まれません。
  * `signal`: `Symbol`、実験的取得データのタイプとキー名、例：`:area`。
  * `rel_sig`: `Symbol`、相対信号のキー名。
  * `est_conc`: `Symbol`、推定濃度のキー名。
  * `true_conc`: `Symbol`、真の濃度のキー名。
  * `acc`: `Symbol`、精度のキー名。
  * `pointlevel`: `Vector{Int}`、各ポイントをレベルにマッチさせます。`conctable`にレベルが1つしかない場合は空であることがあります。
  * `conctable`: `C <: AbstractDataTable{<: A, Int}`、各レベルの濃度データを含みます。サンプルは整数でなければなりません。1つのレベルは`SingleCalibration`を使用することを示します。
  * `signaltable`: `D <: AbstractDataTable{A}`、各ポイントの信号を含みます。信号データが不要な場合は`nothing`にすることができます。

# プロパティ

  * `analyte`: `AbstractVector{A}`、ユーザー定義型の分析物、`analytetable.analyte`と同一です。
  * `isd`: `AbstractVector{A}`、内部標準である分析物。
  * `nonisd`: `AbstractVector{A}`、内部標準でない分析物。
  * `point`: `AbstractVector{S}`、キャリブレーションポイント、`sampleobj(signaltable)`と同一です。`signaltable`が`nothing`の場合、この値も`nothing`です。
  * `level`: `AbstractVector{Int}`、キャリブレーションレベル、`sampleobj(conctable)`と同一です。
