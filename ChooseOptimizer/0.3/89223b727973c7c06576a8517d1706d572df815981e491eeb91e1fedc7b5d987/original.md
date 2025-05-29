```
set_solver(OPT_NAME::Module = HiGHS, verb::Bool = false)
```

sets the optimization solver to be used.

This automatically invokes `clear_solver_options()` and  then sets the appropriate option for verbose output based on the value of the (optional) `verb` argument.
