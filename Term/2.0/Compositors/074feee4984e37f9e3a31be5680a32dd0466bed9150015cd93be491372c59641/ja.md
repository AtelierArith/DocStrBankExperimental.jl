```
mutable struct Compositor
    layout::Expr
    elements::Dict{Symbol,LayoutElement}
end
```

レイアウトコンポジタは、式から更新可能なレイアウトを作成します。
