```
get_variables(method::AbstractReactionMethod; filterfn = v -> true) -> Vector{VariableReaction}
```

`method.varlists` から `VariableReactions` をフラットなベクターとして取得し、オプションで `filterfn` に一致するものに制限します。
