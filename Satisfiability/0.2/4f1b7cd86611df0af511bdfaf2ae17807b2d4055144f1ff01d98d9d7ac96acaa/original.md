```
assign!(e::AbstractExpr, assignment::Dict)
assign!(exprs::Array, assignment::Dict)
```

Assigns the values of expressions in e (including nested expressions and variables) using `assignment`, a Dict where every key is a string corresponding to an expression name, and the corresponding value is its satisfying assignment.

`assign!` is intended to be useful in two cases.

1. Using an `assignment` dict returned by `sat!` in interactive mode.This looks like:

```julia
    # define some exprs
    interactive_solver = open(solver)
    assert(interactive_solver, exprs...)
    status, assignment = sat!(interactive_solver)
    assign!.(exprs, assignment)
```

2. Using an `assignment` dict returned by `parse_model`, which parses the raw SMT-LIB output of "(get-model)".
