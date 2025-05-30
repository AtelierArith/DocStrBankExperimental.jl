```
edges_interval(genealogy, ωs)
edges_interval(genealogy, ωs, buffer, visited, root = mrca(genealogy), min_latitude = zero(Float64), block_predicates = [])
```

系譜のエッジを [`EdgesInterval`](@ref) を介して反復処理します。

`buffer` は `CheapStack` または新しく構築された `CheapStack` のバッファとして使用される `UnsafeArray` のいずれかです。

# メソッド

```julia
edges_interval(
    genealogy,
    ωs,
    buffer,
    visited,
    root,
    min_latitude;
    block_predicates
)
edges_interval(genealogy, ωs, buffer, visited, root; ...)
edges_interval(genealogy, ωs, buffer, visited; ...)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:1092`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。

```julia
edges_interval(genealogy, ωs)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:1097`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。
