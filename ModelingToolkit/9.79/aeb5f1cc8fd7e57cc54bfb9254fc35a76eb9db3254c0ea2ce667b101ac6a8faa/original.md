```julia
DelayParentScope(
    sym::Union{Symbolics.Num, SymbolicUtils.Symbolic, Symbolics.Arr{Symbolics.Num}}
) -> Any

```

Apply `DelayParentScope` to `sym`, with a delay of `1` and `parent` being `LocalScope`.
