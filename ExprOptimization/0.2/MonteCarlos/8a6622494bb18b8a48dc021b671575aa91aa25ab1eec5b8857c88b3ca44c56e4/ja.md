```
optimize(p::MonteCarlo, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)

モンテカルロを使用した式木の最適化。パラメータは p、文法は 'grammar'、開始シンボルは typ、損失関数は 'loss' です。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode, grammar::Grammar).
```
