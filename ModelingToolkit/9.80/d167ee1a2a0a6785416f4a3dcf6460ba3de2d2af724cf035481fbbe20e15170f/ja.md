```julia
ParentScope(
    sym::Union{Symbolics.Num, SymbolicUtils.Symbolic, Symbolics.Arr{Symbolics.Num}}
) -> Any

```

`sym`に`ParentScope`を適用し、`parent`を`LocalScope`とします。
