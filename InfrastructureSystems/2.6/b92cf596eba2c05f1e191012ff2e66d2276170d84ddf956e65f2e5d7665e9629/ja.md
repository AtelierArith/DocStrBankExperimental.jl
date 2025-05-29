```
mutable struct Probabilistic <: Forecast
    name::String
    resolution::Dates.Period
    percentiles::Vector{Float64}
    data::SortedDict
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

コンポーネント内の特定のデータフィールドに対する確率的予測。

# 引数

  * `name::String`: ユーザー定義の名前
  * `resolution::Dates.Period`: 予測の解像度
  * `percentiles::Vector{Float64}`: 確率的予測のパーセンタイル
  * `data::SortedDict`: タイムスタンプ - スケーリングファクター
  * `scaling_factor_multiplier::Union{Nothing, Function}`: 時系列データがスケーリングファクターである場合に適用されます。関連するコンポーネントで呼び出されて値を変換します。
  * `internal::InfrastructureSystemsInternal`
