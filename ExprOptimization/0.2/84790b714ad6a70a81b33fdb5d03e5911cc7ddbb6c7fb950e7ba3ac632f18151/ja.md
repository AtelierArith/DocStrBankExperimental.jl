```
optimize(p::ExprOptAlgorithm, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

式最適化のメインエントリ。最適化アルゴリズムを指定するために具体的な ExprOptAlgorithm を使用します。文法と開始シンボル、typ、および損失関数を使用して最適化します。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode)。
