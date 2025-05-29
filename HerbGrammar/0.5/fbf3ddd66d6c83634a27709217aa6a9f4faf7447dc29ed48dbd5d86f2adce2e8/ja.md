```
contains_returntype(node::RuleNode, grammar::AbstractGrammar, sym::Symbol, maxdepth::Int=typemax(Int))
```

ノード `node` に根ざした木が、指定された戻り値の型または非終端記号を持つ、深さが `maxdepth` より小さいノードを少なくとも1つ含む場合は真を返します。
