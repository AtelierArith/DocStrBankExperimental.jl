```
abstract type ProgramIterator
```

すべての可能な探索戦略のための汎用イテレータ。すべてのイテレータは以下のフィールドを持つことが期待されます：

  * `grammar::ContextSensitiveGrammar`: 探索する文法
  * `sym::Symbol`: 探索を開始する開始記号を定義
  * `max_depth::Int`: プログラムツリーの最大深さ
  * `max_size::Int`: プログラムツリーの最大[`AbstractRuleNode`](@ref)数
  * `max_time::Int`: イテレータがかかる最大時間
  * `max_enumerations::Int`: 最大列挙数
