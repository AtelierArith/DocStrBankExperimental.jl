```
sample(root::RuleNode, typ::Symbol, grammar::AbstractGrammar,
                      maxdepth::Int=typemax(Int))
```

与えられた戻り値の型 typ に基づいて、maxdepth に制限されたランダムなノードを均等に選択します。
