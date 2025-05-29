```
determine_topology(path, options::Options)
determine_topology(path; kwargs...)
```

`path`にあるファイルで記述された構造のトポロジーを計算します。これは、`topological_genome(UnderlyingNets(parse_chemfile(path, options)))`を呼び出すことと正確に同等です。

[`InterpenetratedTopologyResult`](@ref)を返します。
