```
vLine(
    height::Int;
    style::String = TERM_THEME[].line,
    box::Symbol = TERM_THEME[].box,
    char::Union{Char,Nothing} = nothing,
)
```

Create a `vLine` given a height and, optionally, style information.
