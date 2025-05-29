```julia
set_system!(
    results::PowerSimulations.SimulationProblemResults,
    system::AbstractString
)

```

結果インスタンスにシステムを設定します。

システムUUIDが不正な場合はInvalidValueをスローします。

# 引数

  * `results::SimulationProblemResults`: 結果オブジェクト
  * `system::AbstractString`: システムjsonファイルへのパス

# 例

```julia
julia > set_system!(res, "my_path/system_data.json")
```
