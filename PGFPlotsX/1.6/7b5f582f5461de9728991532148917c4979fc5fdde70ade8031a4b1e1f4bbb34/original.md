```
print_tex(io, elt, [container])
```

Print `elt` to `io` as LaTeX code. The optional third argument allows methods to work differently depending on the container.

`print_tex(String, ...)` returns the LaTeX code as a `String`.

This method should indent as if at the top level, containers indent their contents as necessary. See [`print_indent`](@ref).
