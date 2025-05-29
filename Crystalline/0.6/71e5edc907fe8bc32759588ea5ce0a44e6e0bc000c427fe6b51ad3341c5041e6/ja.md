```
is_abelian(ops::AbstractVector{SymOperation}, [cntr::Union{Char, Nothing}])  -->  Bool
```

グループ `ops` から構成される群がアーベル群であるかどうかを返します。

群 $G$ がアーベル群であるためには、そのすべての要素が互いに可換である必要があります。すなわち、すべての $g,h ∈ G$ に対して $g = hgh^{-1}$ である必要があります。

[`classes`](@ref) における設定引数 `cntr` の議論を参照してください。
