```
optimize(p::GrammaticalEvolution, grammar::Grammar, typ::Symbol, loss::Function; kwargs...)
```

文法進化アルゴリズムで、パラメータ p、文法 'grammar'、開始シンボル typ、および損失関数 'loss' を使用します。損失関数は次の形式を持ちます: los::Float64=loss(node::RuleNode, grammar::Grammar)。

参照: Ryan, Collins, O'Neil, "Grammatical Evolution: Evolving Programs for an Arbitrary Language",      in European Conference on Genetic Programming, Spring, 1998, pp. 83-96. 
