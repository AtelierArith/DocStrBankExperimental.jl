```
Reformer <: AbstractReformer
```

起動およびシャットダウンの時間とコストを持つネットワークノードで、リフォーマー技術の説明に使用されるべきです。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は容量使用に対する変動運営費です。
  * **`opex_fixed::TimeProfile`** は設置された容量に対する固定運営費です。
  * **`input::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ入力 [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`output::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ生成された [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`data::Array{Data}`** は追加データの配列（例：投資用）です。
  * **`load_limits::LoadLimits`** は電解槽の利用負荷に対する制限です。 [`LoadLimits`](@ref) は実際の負荷に対する下限と上限の両方を提供できます。
  * **`startup::CommitParameters`** は起動状態制約のためのパラメータです。
  * **`shutdown::CommitParameters`** はシャットダウン状態制約のためのパラメータです。
  * **`offline::CommitParameters`** はオフライン状態制約のためのパラメータです。
  * **`ramp_limit::AbstractRampParameters`** は容量使用の許可される変化の制限です。

!!! note
      * [`CaptureEnergyEmissions`](@extref EnergyModelsBase.CaptureEnergyEmissions) を通じてCO₂捕集を導入する場合、CO₂インスタンスを出力として追加する必要があります。これは、`output` 辞書を通じて変数 `:output` を宣言するためです。
      * 指定された起動、シャットダウン、およびオフラインコストは、設置された容量と1つの運用期間の期間に対して相対的です。
      * レート制限は、設置された容量と1つの運用期間の期間に対して相対的です。

