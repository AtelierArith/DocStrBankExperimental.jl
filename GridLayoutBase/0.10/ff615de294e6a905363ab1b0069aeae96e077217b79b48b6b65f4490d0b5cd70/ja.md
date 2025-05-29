```
function GridLayout(nrows::Integer, ncols::Integer;
    parent = nothing,
    rowsizes = nothing,
    colsizes = nothing,
    addedrowgaps = nothing,
    addedcolgaps = nothing,
    alignmode = Inside(),
    equalprotrusiongaps = (false, false),
    bbox = nothing,
    width = Auto(),
    height = Auto(),
    tellwidth::Bool = true,
    tellheight::Bool = true,
    halign = :center,
    valign = :center,
    default_rowgap = get_default_rowgap(),
    default_colgap = get_default_colgap(),
    kwargs...)
```

`nrows` 行と `ncols` 列を持つオプションの親 `parent` を持つ `GridLayout` を作成します。
