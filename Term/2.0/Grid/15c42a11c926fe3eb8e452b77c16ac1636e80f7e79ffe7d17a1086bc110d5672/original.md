```
grid(
    rens::Union{AbstractVector,Tuple,NamedTuple};
    placeholder::Union{Nothing,AbstractRenderable} = nothing,
    placeholder_size::Union{Nothing,Tuple} = nothing,
    aspect::Union{Nothing,Number,NTuple} = nothing,
    layout::Union{Nothing,Tuple,Expr} = nothing,
    show_placeholder::Bool = false,
    pad::Union{Tuple,Integer} = 0,
    order::Symbol = :row,
)
```

# Description

Construct a grid from an iterable (`AbstractVector`, `Tuple`, `NamedTuple`).

Lays out the renderables to create a grid with the desired aspect ratio or layout (number of rows, number of columns, or one left free with `nothing`). Complex layout is supported using compositor expressions.

# Arguments

`placeholder`: placeholder for empty grid components. `placeholder_size`: size of the auto-placeholder. `aspect`: target grid aspect ratio. `layout`: tuple (rows, cols) final size or complex expression. `show_placeholder`: display/hide placeholder(s). `pad`: additional padding between layout components. `order`: `:row` for row major input iteration (default) or `:col` for column major.
