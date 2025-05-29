```
sample(root::RuleNode, typ::Symbol, grammar::Grammar,
                      maxdepth::Int=typemax(Int))
```

指定された戻り値の型 typ の均一にランダムなノードを選択し、maxdepth に制限します。
