```
facet_grid(;rows, cols, scales = "fixed", switch = "none")
```

facet*grid() forms a matrix of panels defined by row and column faceting variables. It is most useful when you have two discrete variables, and all combinations of the variables exist in the data. If you have only one variable with many levels, try facet*wrap().

# Arguments

  * `rows` (required): Variable to use for the rows of the matrix
  * `cols` (required): Variable to use for the columns of the matrix
  * `scales` (optional): Should the scales be fixed or free? Options: "free", "free*x", "free*y"
  * `switch` (optional): Flip the labels from their default "top and right". Options: "x", "y", "both".
