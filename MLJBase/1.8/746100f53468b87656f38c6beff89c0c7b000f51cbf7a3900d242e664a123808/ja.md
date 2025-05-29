```
evaluate!(mach; resampling=CV(), measure=nothing, options...)
```

データ内の教師ありモデルをラップする機械 `mach` の性能を、指定された `resampling` 戦略（デフォルトは6分割交差検証）と `measure` を使用して推定します。`measure` は単一の測定またはベクトルであることができます。[`PerformanceEvaluation`](@ref) オブジェクトを返します。

利用可能なリサンプリング戦略は `CV`、`Holdout`、`InSample`、`StratifiedCV` および `TimeSeriesCV` です。`resampling` がこれらのいずれかのインスタンスでない場合、`(train_rows, test_rows)` の形式のタプルのベクトルが期待されます。たとえば、次のように設定すると

```julia
resampling = [(1:100, 101:200),
              (101:200, 1:100)]
```

最初の200行のデータを使用した2分割交差検証が行われます。

複数の観測を消費できると仮定される、[StatisticalMeasuresBase.jl](https://juliaai.github.io/StatisticalMeasuresBase.jl/dev/) API に準拠した任意の測定を提供できます。

`evaluate!` はミューテーションを行いますが、`mach.model` と `mach.args` はミューテーションされません。

# 追加のキーワードオプション

  * `rows` - トレーニングとテストのフォールドが構築される観測インデックスのベクトル（デフォルトはすべての観測）
  * `operation`/`operations=nothing` - `predict`、`predict_mean`、`predict_mode`、`predict_median`、または `predict_joint` のいずれか、または `measure`/`measures` と同じ長さのこれらのベクトル。指定しない場合は自動的に推測されます。たとえば、`model` が確率的予測器であり、`measure` がリテラル（ポイント）ターゲット予測を期待する場合、`Multiclass` ターゲットには `predict_mode` が使用されます。実際に適用された操作は、返されたオブジェクトの `operation` フィールドから確認できます。
  * `weights` - 測定をサポートするサンプルごとの `Real` 重み（トレーニングに使用される重み、たとえば `mach = machine(model, X, y, w)` の `w` とは混同しないでください）。
  * `class_weights` - 分類問題において、これをサポートする測定に使用するためのクラスごとの `Real` 重みの辞書（トレーニングに使用される重み、たとえば `mach = machine(model, X, y, w)` の `w` とは混同しないでください）。
  * `repeats::Int=1`: 繰り返し（モンテカルロ）リサンプリングのために高い値に設定します。たとえば、`repeats = 10` の場合、`resampling = CV(nfolds=5, shuffle=true)` は評価とその後の集約のために合計50の `(train, test)` ペアを生成します。
  * `acceleration=CPU1()`: 加速/並列化オプション；`CPU1`（単一スレッド計算）、`CPUThreads`（マルチスレッド計算）または `CPUProcesses`（マルチプロセス計算）のいずれかのインスタンスを指定できます；デフォルトは `default_resource()` です。これらのタイプは ComputationalResources.jl に属します。
  * `force=false`: 各トレーニングイベントのコールドリスタートを強制するには `true` に設定します。
  * `verbosity::Int=1` ロギングレベル；負の値も可能です。
  * `check_measure=true`: 測定がモデルと互換性があるかどうかを確認するかどうか。すべての非互換性をキャッチするわけではありません。
  * `per_observation=true`: 個々の観測の推定を計算するかどうか；`false` の場合、返されたオブジェクトの `per_observation` フィールドは `missing` で埋められます。`false` に設定すると、計算時間と割り当てが減少する可能性があります。
  * `logger=default_logger()` - 機械学習トラッキングプラットフォームに結果を転送するためのロガーオブジェクト；詳細については [`default_logger`](@ref) を参照してください。
  * `compact=false` - `true` の場合、返された評価オブジェクトは次のフィールドを除外します：`fitted_params_per_fold`、`report_per_fold`、`train_test_rows`。

[`evaluate`](@ref)、[`PerformanceEvaluation`](@ref)、[`CompactPerformanceEvaluation`](@ref) も参照してください。
