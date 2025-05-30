```
get_variables(method::AbstractReactionMethod; filterfn = v -> true) -> Vector{VariableReaction}
```

`method.varlists` から `filterfn` に一致するものをオプションで制限しながら、フラットなベクターとして VariableReactions を取得します。
