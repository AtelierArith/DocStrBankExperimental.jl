```julia
read_realized_variable(
    res::PowerSimulations.SimulationProblemResults,
    variable::AbstractString;
    kwargs...
) -> Any

```

問題の各時間ステップに対する要求された変数の最終値を返します。

意思決定問題の結果は `Dict{DateTime, DataFrame}` で返されます。

エミュレーション問題の結果は `DataFrame` で返されます。

意思決定問題の場合は `initial_time` と `count` を指定することで、エミュレーション問題の場合は `start_time` と `len` を指定することで、返されるデータサイズを制限できます。

データをメモリに事前ロードするには、[`load_results!`](@ref) も参照してください。

# 引数

  * `variable::Union{String, Tuple}`: 変数名を文字列または変数タイプとデバイスタイプのタプルとして指定します。
  * `initial_time::Dates.DateTime`: 要求された結果の初期時間。意思決定問題のみ。
  * `count::Int`: 結果の数。意思決定問題のみ。
  * `start_time::Dates.DateTime`: 要求された結果の開始時間。エミュレーション問題のみ。
  * `len::Int`: 各 DataFrame の行数。エミュレーション問題のみ。

# 例

```julia
julia > read_realized_variable(results, "ActivePowerVariable__ThermalStandard")
julia > read_realized_variable(results, (ActivePowerVariable, ThermalStandard))
```
