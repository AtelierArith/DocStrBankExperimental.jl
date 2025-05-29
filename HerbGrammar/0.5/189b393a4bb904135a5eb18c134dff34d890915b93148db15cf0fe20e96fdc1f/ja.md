```
iseval(grammar::AbstractGrammar, index::Int)::Bool
```

ルールインデックスにある生成規則が特別な _() eval 関数を含む場合は true を返します。

!!! compat
    即時評価機能は、まだほとんどの Herb.jl ではサポートされていません。

