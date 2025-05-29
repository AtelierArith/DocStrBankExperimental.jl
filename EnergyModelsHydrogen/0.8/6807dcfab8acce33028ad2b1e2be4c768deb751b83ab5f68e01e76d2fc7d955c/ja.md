```
SimpleElectrolyzer <: AbstractElectrolyzer
```

最小および最大負荷、ならびにスタック交換を持つシンプルな電解槽ノードの説明。劣化は計算されますが、効率計算には使用されません。

`NetworkNode`と比較して新しいフィールド: `min_load`, `max_load`, `degradation_rate`, `stack_lifetime`, および `stack_replacement_cost`。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`cap::TimeProfile`** は設置された容量です。
  * **`opex_var::TimeProfile`** は容量使用あたりの変動運営費用です。
  * **`opex_fixed::TimeProfile`** は設置された容量あたりの固定運営費用です。
  * **`input::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ入力 [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`output::Dict{<:Resource, <:Real}`** は変換値 `Real` を持つ生産された [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`data::Vector{Data}`** は追加データ（例: 投資用）です。
  * **`load_limits::LoadLimits`** は電解槽の利用負荷に関する制限です。 [`LoadLimits`](@ref) は実際の負荷に対する下限および上限を提供できます。
  * **`degradation_rate::Real`** は劣化による効率のパーセンテージの低下で、%/1000 h で表されます。
  * **`stack_replacement_cost::TimeProfile`** は電解槽スタックの交換コストです。
  * **`stack_lifetime::Real`** は総運用スタック寿命です。

!!! note
      * 定格電解槽効率は `input` と `output` の組み合わせを通じて捉えられます。
      * 固定および変動運営費用は常に設置された容量とその使用に関連しています。これは、容量を入力を通じて1の値で定義した場合、変動運営費用が必要な電力を通じて計算されることを意味します。
      * スタック交換は、戦略的期間中にのみ行うことができ、最初の運用期間に行われます。これは、戦略的期間が繰り返されると問題が発生するためです。

