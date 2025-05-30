```
Electrolyzer <: AbstractElectrolyzer
```

最小負荷と最大負荷、劣化およびスタック交換を持つ電解槽ノードの説明。

新しいフィールド: `min_load`, `max_load`, `stack_lifetime`, `stack_replacement_cost`, および `degradation_rate`。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は使用された容量あたりの変動運営費です（変数 `:cap_use` を通じて）。
  * **`opex_fixed::TimeProfile`** は設置された容量あたりの固定運営費です。
  * **`input::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ入力 [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`output::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ生成された [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`data::Vector{Data}`** は追加データ（例：投資用）です。
  * **`load_limits::LoadLimits`** は電解槽の利用負荷に関する制限です。 [`LoadLimits`](@ref) は実際の負荷に対する下限と上限の両方を提供できます。
  * **`degradation_rate::Real`** は劣化による効率の低下の割合で、%/1000 h で表されます。
  * **`stack_replacement_cost::TimeProfile`** は電解槽スタックの交換コストです。
  * **`stack_lifetime::Real`** は総運用スタック寿命です。

!!! note
      * 名目上の電解槽効率は `input` と `output` の組み合わせを通じて捉えられます。
      * 固定および変動運営費は常に設置された容量とその使用に関連しています。これは、容量を1の値を通じて入力で定義した場合、変動運営費は必要な電力を通じて計算されることを意味します。
      * スタックの交換は、戦略的な期間中にのみ行うことができます。最初の運用期間においてです。これは、戦略的な期間が繰り返されると問題が発生する可能性があるためです。

