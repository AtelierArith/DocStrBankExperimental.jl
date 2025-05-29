```julia
print_tex(io, str)

```

Print a string *as is*, terminated with a newline.

!!! note
    This is used as a workaround for LaTeX code that does not have a corresponding type, eg as elements in [`Axis`](@ref). `raw` or `LaTeXStrings` are useful to avoid piling up backslashes. The newline is added to separate tokens.

