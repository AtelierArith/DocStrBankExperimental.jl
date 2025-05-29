```
mutable struct Deterministic <: AbstractDeterministic
    name::String
    data::SortedDict
    resolution::Dates.Period
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

コンポーネント内の特定のデータフィールドに対する決定論的予測。

# 引数

  * `name::String`: ユーザー定義の名前
  * `data::SortedDict`: タイムスタンプ - スケーリングファクター
  * `resolution::Dates.Period`: 予測の解像度
  * `scaling_factor_multiplier::Union{Nothing, Function}`: 時系列データがスケーリングファクターである場合に適用されます。関連するコンポーネントで呼び出され、値を変換します。
  * `internal::InfrastructureSystemsInternal`
