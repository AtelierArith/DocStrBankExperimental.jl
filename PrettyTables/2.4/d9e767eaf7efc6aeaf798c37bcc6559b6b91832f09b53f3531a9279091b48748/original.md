```
LatexHighlighter
```

Defines the default highlighter of a table when using the LaTeX backend.

# Fields

  * `f::Function`: Function with the signature `f(data, i, j)` in which should return `true`   if the element `(i, j)` in `data` must be highlighted, or `false` otherwise.
  * `fd`: A function with the signature `f(data, i, j, str)::String` in which `data` is the   matrix, `(i, j)` is the element position in the table, and `str` is the data converted   to string. This function must return a string that will be placed in the cell.

# Remarks

This structure can be constructed using two helpers:

```
LatexHighlighter(f::Function, envs::Union{String, Vector{String}})

LatexHighlighter(f::Function, fd::Function)
```

The first will apply recursively all the LaTeX environments in `envs` to the highlighted text whereas the second let the user select the desired decoration by specifying the function `fd`.

Thus, for example:

```
LatexHighlighter((data, i, j)->true, ["textbf", "small"])
```

will wrap all the cells in the table in the following environment:

```
\textbf{\small{<Cell text>}}
```
