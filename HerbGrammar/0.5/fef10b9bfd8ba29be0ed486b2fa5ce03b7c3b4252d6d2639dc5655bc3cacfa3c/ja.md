```
mindepth(grammar::AbstractGrammar, typ::Symbol, dmap::AbstractVector{Int})
```

指定された非終端記号に対して達成可能な最小深さを返します。最小深さは、`typ`を開始記号として使用して作成できる最も低い木の深さです。`dmap`は[`mindepth_map`](@ref)から取得できます。
