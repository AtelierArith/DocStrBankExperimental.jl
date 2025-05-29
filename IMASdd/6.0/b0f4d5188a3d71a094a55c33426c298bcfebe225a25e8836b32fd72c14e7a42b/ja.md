```
parent(@nospecialize(ids::Union{IDS,IDSvector}; IDS_is_absolute_top::Bool=false, error_parent_of_nothing::Bool=true)
```

階層内の親 IDS/IDSvector を返します

`IDS_is_absolute_top=true` の場合、dd() の代わりに `nothing` を返します

`error_parent_of_nothing=true` の場合、`parent(nothing)` を呼び出すと単に `nothing` を返します
