```
optimize(p::PIPE, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

PIPEアルゴリズムを使用した式木の最適化。パラメータはp、文法'grammar'、開始シンボルtyp、損失関数'loss'です。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode, grammar::Grammar)。
