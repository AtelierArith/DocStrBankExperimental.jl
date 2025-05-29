```julia
DelayParentScope(
    sym::Union{Symbolics.Num, SymbolicUtils.Symbolic, Symbolics.Arr{Symbolics.Num}}
) -> Any

```

`sym`に`DelayParentScope`を適用し、遅延を`1`、`parent`を`LocalScope`とします。
