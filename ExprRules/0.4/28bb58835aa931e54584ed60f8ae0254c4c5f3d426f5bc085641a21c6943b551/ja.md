```
contains_returntype(node::RuleNode, grammar::Grammar, sym::Symbol, maxdepth::Int=typemax(Int))
```

ノードで根付けられた木が、指定された戻り型を持つ深さがmaxdepth未満のノードを少なくとも1つ含む場合、trueを返します。
