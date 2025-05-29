```
AbstractGrammar
```

すべての文法を表す抽象型です。すべての文法構造体は、少なくとも以下の属性を持つと仮定されています。

  * `rules::Vector{Any}`: ルールの右辺（サブエクスプレッション）のリスト。
  * `types::Vector{Symbol}`: ルールの左辺（型、すべてのシンボル）のリスト。
  * `isterminal::BitVector`: ビット `i` がルール `i` が終端であるかどうかを表すビットベクター。
  * `iseval::BitVector`: ビット `i` がルール `i` が評価ルールであるかどうかを表すビットベクター。
  * `bytype::Dict{Symbol,Vector{Int}}`: 型をその型のすべてのルールにマッピングする辞書。
  * `domains::Dict{Symbol, BitVector}`: 型をドメインビットベクターにマッピングする辞書。ドメインビットベクターは、`i` 番目のルールがこの型である場合に限り、ビット `i` が真に設定されます。
  * `childtypes::Vector{Vector{Symbol}}`: 各ルールの子の型のリスト。

ルールが終端である場合、対応するリストは空です。

  * `log_probabilities::Union{Vector{Real}, Nothing}`: 各ルールの確率のリスト。

文法が非確率的である場合、リストは `nothing` である可能性があります。

具体的な型については、`HerbGrammar` モジュール内の `ContextSensitiveGrammar` を参照してください。
