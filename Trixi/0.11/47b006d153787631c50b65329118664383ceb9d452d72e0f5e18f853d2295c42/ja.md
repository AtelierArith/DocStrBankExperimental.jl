```
adapt_to_mesh_level!(u_ode, semi, level)
adapt_to_mesh_level!(sol::Trixi.TrixiODESolution, level)
```

[`adapt_to_mesh_level`](@ref)と同様ですが、解と半離散化の一部（メッシュとキャッシュ）をその場で修正します。
