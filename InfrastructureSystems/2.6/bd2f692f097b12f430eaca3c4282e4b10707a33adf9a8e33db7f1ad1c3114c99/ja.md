```
mutable struct Scenarios <: Forecast
    name::String
    resolution::Dates.Period
    scenario_count::Int64
    data::SortedDict
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

コンポーネント内の特定のデータフィールドに対する離散シナリオベースの時系列。

# 引数

  * `name::String`: ユーザー定義の名前
  * `resolution::Dates.Period`: 予測解像度
  * `scenario_count::Int64`: シナリオの数
  * `data::SortedDict`: タイムスタンプ - スケーリングファクター
  * `scaling_factor_multiplier::Union{Nothing, Function}`: 時系列データがスケーリングファクターである場合に適用されます。関連するコンポーネントで呼び出されて値を変換します。
  * `internal::InfrastructureSystemsInternal`
