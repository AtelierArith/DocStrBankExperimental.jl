```
league_catch_cp(catch_name::AbstractString, league_cp::Int, as_name::AbstractString = catch_name; kwargs...) → cparray
league_catch_cp(pd::Species, league_cp::Int, as::Species = pd; kwargs...) → cparray
```

IVsによってインデックス付けされた3D `cparray`を返し、進化して`as_uid`になるときに、`league_cp`以下の最大CPを野生捕獲するためのCPを返します。
