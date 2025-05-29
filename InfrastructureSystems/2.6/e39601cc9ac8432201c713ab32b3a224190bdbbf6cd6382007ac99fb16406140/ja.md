```
mutable struct SingleTimeSeries <: StaticTimeSeries
    name::String
    data::TimeSeries.TimeArray
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

コンポーネントの特定のデータフィールドに対する単一の列の時系列データ。

予測とは対照的に、これは歴史的な測定値や実現、または単一のシナリオ（例：気象年や異なる入力仮定）のような、1つの連続した時系列を表すことができます。

# 引数

  * `name::String`: ユーザー定義の名前
  * `data::TimeSeries.TimeArray`: タイムスタンプ - スケーリングファクター
  * `resolution::Dates.Period`: 時系列のステップ間の時間の長さ。解像度は時系列全体で同じでなければなりません
  * `scaling_factor_multiplier::Union{Nothing, Function}`: 時系列データがスケーリングファクターである場合に適用されます。関連するコンポーネントで呼び出され、値を変換します。
  * `internal::InfrastructureSystemsInternal`
