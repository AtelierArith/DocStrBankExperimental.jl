```julia
struct Branch
```

静的ブランチ属性のための型。ブランチには0から2のブレークポイントがある可能性があるため、`break_points`および`penalties`フィールドには可変長の`Tuple`が含まれています。

フィールド:

  * `name::InlineStrings.String31`: ブランチの長い名前
  * `to_bus::InlineStrings.String15`: ブランチが向かうバスの名前
  * `from_bus::InlineStrings.String15`: ブランチが出発するバスの名前
  * `rate_a::Float64`: 基本ケースの電力フロー制限 (pu)
  * `rate_b::Float64`: 緊急シナリオの電力フロー制限 (pu)
  * `is_monitored::Bool`: ブランチが監視されているかどうかを定義するブール値
  * `break_points::Tuple{Float64, Float64}`: ブランチのブレークポイント。ブランチには0、1、または2のブレークポイントがあります。ゼロはブレークポイントがないことを示します
  * `penalties::Tuple{Float64, Float64}`: ブランチの各ブレークポイントに対する価格ペナルティ ($)
  * `resistance::Float64`: ブランチの抵抗 (pu)
  * `reactance::Float64`: ブランチのリアクタンス (pu)
  * `is_transformer::Bool`: ブランチが変圧器であるかどうかを示すブール値
  * `tap::Union{Missing, Float64}`: 変圧器の名目巻線1と2の電圧の比
  * `angle::Union{Missing, Float64}`: 位相シフト角 (ラジアン)
