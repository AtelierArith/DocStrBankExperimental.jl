```julia
read_realized_variables(
    res::PowerSimulations.SimulationProblemResults;
    kwargs...
) -> Dict

```

要求された変数の最終値を問題の各時間ステップに対して返します。

意思決定問題の結果は `Dict{String, Dict{DateTime, DataFrame}}` で返されます。

エミュレーション問題の結果は `Dict{String, DataFrame}` で返されます。

意思決定問題の場合は `initial_time` と `count` を指定することで返されるデータサイズを制限できます。エミュレーション問題の場合は `start_time` と `len` を指定します。

Juliaプロセスが複数のスレッドで開始されている場合、コードは変数を並行して読み取ります。

データをメモリに事前ロードするには、[`load_results!`](@ref) も参照してください。

# 引数

  * `variables::Vector{Union{String, Tuple}}`: 変数名を文字列または変数タイプとデバイスタイプのタプルとして指定します。提供されない場合はすべての変数を返します。
  * `initial_time::Dates.DateTime`: 要求された結果の初期時間。意思決定問題のみ。
  * `count::Int`: 結果の数。意思決定問題のみ。
  * `start_time::Dates.DateTime`: 要求された結果の開始時間。エミュレーション問題のみ。
  * `len::Int`: 各DataFrameの行数。エミュレーション問題のみ。

# 例

```julia
julia > variables_as_strings =
    ["ActivePowerVariable__ThermalStandard", "ActivePowerVariable__RenewableDispatch"]
julia > variables_as_types =
    [(ActivePowerVariable, ThermalStandard), (ActivePowerVariable, RenewableDispatch)]
julia > read_realized_variables(results, variables_as_strings)
julia > read_realized_variables(results, variables_as_types)
```
