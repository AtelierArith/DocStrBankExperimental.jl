```
mutable struct Compositor
    layout::Expr
    elements::Dict{Symbol,LayoutElement}
end
```

A layout compositor, creates an updatable layout from an expression.
