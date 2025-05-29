```
interactive_solver = open(Z3()) # open an InteractiveSolver process
status, values = sat!(interactive_solver, exprs...) # check satisfiability of exprs
```

When working with an InteractiveSolver process, issues the `(check-sat)` command. The optional `exprs`, if provided, will be assumed when `(check-sat)` is issued but **not** asserted on the stack. This is equivalent to the SMT-LIB `(check-sat-assuming expr1, expr2,...)` command.

If no assertions have been made, sat! throws an error.

**Note that in this mode, sat! can only set the values of exprs provided in the function call** That means if you `assert(expr1)` and then call `sat!(interactive_solver, expr2)`, `value(expr1)` will be `nothing` **even if the problem is SAT**. To alleviate this, `sat!` returns `(status, values)` where `values` is a Dict of variable names and satisfying assignments. To assign the values of `expr1`, call `assign!(values, expr1)`.

Optional keyword arguments:

  * `logic`: Manually set the solver logic. Must be a string corresponding to a [valid SMT-LIB logic](http://smtlib.cs.uiowa.edu/logics.shtml). If you're unsure how to set this option, don't set it - most solvers can infer the logic to use on their own!
  * `line_ending::String`: The line ending to use after each SMT-LIB command. Defaults to "\r\n" on Windows and "\n" everywhere else.
