```
nlive!(counts, genealogy, lats, ωs[, stack]; block_predicates = [], buffer = default_buffer())
```

与えられた緯度における（周辺的な）系譜の生存エッジの数。

カウントは `counts` に格納され、初めは0で満たされています。 `lats` は `counts` と同じサイズでなければなりません。

`block_predicate` と `stack` は直接 [`edges_interval`](@ref) に渡されます。

また、[`nlive`](@ref) も参照してください。

# メソッド

```julia
nlive!(
    counts,
    genealogy,
    lats,
    ωs,
    stack;
    block_predicates,
    buffer
)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:1163`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。

```julia
nlive!(
    counts,
    genealogy,
    lats,
    ωs;
    block_predicates,
    buffer
)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:1192`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。
