```
normalize!(grammar::ContextSensitiveGrammar, type::Union{Symbol, Nothing}=nothing)
```

確率的 [`ContextSensitiveGrammar`](@ref) の確率を正規化するための関数です。オプションの `type` 引数が提供されている場合、そのタイプのルールのみが正規化されます。文法が確率的でない場合、すなわち `grammar.log_probabilities==nothing` の場合、均一分布が初期化されます。
