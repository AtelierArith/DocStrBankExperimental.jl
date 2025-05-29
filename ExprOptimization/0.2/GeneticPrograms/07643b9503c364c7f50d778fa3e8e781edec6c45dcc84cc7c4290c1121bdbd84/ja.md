```
optimize(p::GeneticProgram, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

遺伝的プログラミングを使用した式木の最適化。パラメータは p、文法 'grammar'、開始シンボル typ、損失関数 'loss' です。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode, grammar::Grammar)。
