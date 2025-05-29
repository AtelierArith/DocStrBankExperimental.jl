```
rand(::Type{RuleNode}, grammar::AbstractGrammar, typ::Symbol, dmap::AbstractVector{Int}, max_depth::Int=10)
```

ランダムな [`RuleNode`](@ref)、すなわち、ルートタイプ typ と最大深さ max_depth に従って深さマップ dmap によってガイドされた式ツリーを生成します。
