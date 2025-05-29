判断を実行した結果を保存します。詳細は[`judge`](@ref)を参照してください。

以下の（未エクスポートの）メソッドは`BenchmarkJudgement`（以下`judgement`として記述）に定義されています：

  * `target_result(judgement)::BenchmarkResults` - `target`の[`BenchmarkResults`](@ref)。
  * `baseline_result(judgement)::BenchmarkResults` - `baseline`の[`BenchmarkResults`](@ref)。
  * `benchmarkgroup(judgement)::BenchmarkGroup` - 推定結果を含む[`BenchmarkGroup`](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#the-benchmarkgroup-type)

`BenchmarkJudgement`は、関数[`export_markdown`](@ref)を使用してマークダウンにエクスポートできます。

詳細は[`BenchmarkResults`](@ref)を参照してください。
