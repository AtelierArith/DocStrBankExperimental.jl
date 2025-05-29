```
textbox(s::T where T <: AbstractString, pos::Point=O;
    leading = 12,
    linefunc::Function = (linenumber, linetext, startpos, height) -> (),
    alignment=:left)
```
