```
sudoku(n; start= Dictionary{Int, Int}(), modeler = :JuMP)
```

Create a model for the sudoku problem of domain `1:n²` with optional starting values. The `modeler` argument accepts :raw, :MOI, and :JuMP (default), which refer respectively to the solver internal model, the MathOptInterface model, and the JuMP model.

```julia
# Construct a JuMP model `m` and its associated matrix `grid` for sudoku 9×9
m, grid = sudoku(3)

# Same with a starting instance
instance = [
    9  3  0  0  0  0  0  4  0
    0  0  0  0  4  2  0  9  0
    8  0  0  1  9  6  7  0  0
    0  0  0  4  7  0  0  0  0
    0  2  0  0  0  0  0  6  0
    0  0  0  0  2  3  0  0  0
    0  0  8  5  3  1  0  0  2
    0  9  0  2  8  0  0  0  0
    0  7  0  0  0  0  0  5  3
]
m, grid = sudoku(3, start = instance)

# Run the solver
optimize!(m)

# Retrieve and display the values
solution = value.(grid)
display(solution, Val(:sudoku))
```
