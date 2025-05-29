```
get_variables(reaction, localname) -> Vector{VariableReaction}
get_variables(reaction; [filterfn=v->true]) -> Vector{VariableReaction}
```

すべてのReactionMethodsから一致する変数を取得します。
