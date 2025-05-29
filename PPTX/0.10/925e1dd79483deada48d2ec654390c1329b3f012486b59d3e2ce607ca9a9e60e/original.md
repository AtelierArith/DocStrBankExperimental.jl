```julia
TableCell(
    content; # text
    textstyle = TextStyle(),
    color = nothing, # background color of the table element
    anchor = nothing, # anchoring of text in the cell, can be "top", "bottom" or "center"
    lines,
    margins,
)
```

Create a styled TableCell for use inside a table/dataframe.

# Example

```julia
julia> t = TableCell(4; color = :green, textstyle=(color=:blue,))
TableCell
 text is 4
 textstyle has
  color is 0000FF
 background color is 008000

```
