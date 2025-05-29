```julia
DelayParentScope(
    sym::Union{Symbolics.Num, SymbolicUtils.Symbolic, Symbolics.Arr{Symbolics.Num}},
    N
) -> Any

```

`sym`に`N`の遅延を適用し、`parent`を`LocalScope`とします。
