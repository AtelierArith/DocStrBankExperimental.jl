```julia
DelayParentScope(
    sym::Union{Symbolics.Num, SymbolicUtils.Symbolic, Symbolics.Arr{Symbolics.Num}},
    N
) -> Any

```

Apply `DelayParentScope` to `sym`, with a delay of `N` and `parent` being `LocalScope`.
