```
optimize(p::CrossEntropy, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

クロスエントロピー法を用いた式木の最適化。パラメータは p、文法 'grammar'、開始記号 typ、損失関数 'loss' です。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode, grammar::Grammar)

参照: Rubinstein, "Optimization of Computer Simulation Models with Rare Events", European Journal of Operations Research, 99, 89-112, 1197
