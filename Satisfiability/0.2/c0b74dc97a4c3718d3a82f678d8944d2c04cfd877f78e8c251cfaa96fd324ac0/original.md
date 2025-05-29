```
sat!(z::BoolExpr, solver=Z3())
sat!(z1, z2,..., solver=CVC5())
```

Solve the SAT problem using a Solver. If the problem is satisfiable, update the values of all `BoolExprs` in `prob` with their satisfying assignments.

Possible return values are `:SAT`, `:UNSAT`, or `:ERROR`. `prob` is only modified to add Boolean values if the return value is `:SAT`. By default, sat! will reset the values of expressions in `prob` to `nothing` if `prob` is unsatisfiable. To change this behavior use the keyword argument `clear_values_if_unsat`. For example,`sat!(prob, solver=CVC5(), clear_values_if_unsat=false)`.

**Alternate usage:**

```julia
    io = open("some_file.smt")
    status, values = sat!(io::IO, solver=CVC5())
    status, values = sat!(filename::String, solver=CVC5())
```

In io mode, sat! reads the contents of the Julia IO object and passes them to the solver. Thus, users must ensure `read(io)` will return a complete and correct string of SMT-LIB commands, including `(check-sat)` or equivalent. Alternatively, one can pass in a filename to be opened and closed within `sat!`. Because the expressions are not passed into the function, `sat!` returns a dictionary containing the satisfying assignment.

Optional keyword arguments:

  * `solver::Solver`: The Solver to use. Defaults to `Z3()`.
  * `logic`: Manually set the solver logic. Must be a string corresponding to a [valid SMT-LIB logic](http://smtlib.cs.uiowa.edu/logics.shtml). If you're unsure how to set this option, don't set it - most solvers can infer the logic to use on their own!
  * `line_ending::String`: The line ending to use after each SMT-LIB command. Defaults to "\r\n" on Windows and "\n" everywhere else.
  * `clear_values_if_unsat=true`: If true and the expression is unsat, reset its values to `nothing`.
  * `start_commands::String`: Additional SMT-LIB commands to be included before the expression, for example `(set-logic LOGIC)`.
  * `end_commands::String` : Additional SMT-LIB commands to be included after the expression.
