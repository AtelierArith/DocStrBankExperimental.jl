```
sample(::Type{NodeLoc}, root::RuleNode, typ::Symbol, grammar::Grammar)
```

指定されたタイプのノードをツリーから均等にランダムに選択し、その親を使用してサブツリーを置き換えられるようにします。NodeLocを返します。
