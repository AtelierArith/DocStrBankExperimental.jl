```
ContextSensitiveGrammar <: AbstractGrammar
```

コンテキスト感受性文法を表します。制約を持つ[`AbstractGrammar`](@ref)を拡張します。

構成要素は次のとおりです：

  * `rules::Vector{Any}`: ルールの右辺（サブエクスプレッション）のリスト。
  * `types::Vector{Symbol}`: ルールの左辺（タイプ、すべてのシンボル）のリスト。
  * `isterminal::BitVector`: ビット`i`がルール`i`が終端であるかどうかを表すビットベクター。
  * `iseval::BitVector`: ビット`i`がルール`i`が評価ルールであるかどうかを表すビットベクター。
  * `bytype::Dict{Symbol,Vector{Int}}`: タイプをそのタイプのすべてのルールにマッピングする辞書。
  * `domains::Dict{Symbol, BitVector}`: タイプをドメインビットベクターにマッピングする辞書。ドメインビットベクターは、`i`番目のルールがこのタイプである場合に限り、ビット`i`がtrueに設定されます。
  * `childtypes::Vector{Vector{Symbol}}`: 各ルールの子のタイプのリスト。ルールが終端の場合、対応するリストは空です。
  * `bychildtypes::Vector{BitVector}`: 各ルールの同じ子タイプを共有するルールのビットベクター。
  * `log_probabilities::Union{Vector{Real}, Nothing}`: 各ルールの確率のリスト。文法が非確率的な場合、リストは`nothing`にすることができます。
  * `constraints::Vector{AbstractConstraint}`: この文法に従わなければならない制約のリスト。

[`@csgrammar`](@ref)マクロを使用して[`ContextSensitiveGrammar`](@ref)オブジェクトを作成します。[`@pcsgrammar`](@ref)マクロを使用して確率を持つ[`ContextSensitiveGrammar`](@ref)オブジェクトを作成します。
