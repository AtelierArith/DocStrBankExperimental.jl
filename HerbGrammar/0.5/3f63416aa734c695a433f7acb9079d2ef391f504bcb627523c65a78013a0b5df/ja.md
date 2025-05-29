```
isvariable(grammar::AbstractGrammar, node::RuleNode, mod::Module)::Bool
```

`node`によって使用されるルールが変数を表す場合はtrueを返します。

指定されたモジュール内で定義されたシンボルを考慮に入れます。
