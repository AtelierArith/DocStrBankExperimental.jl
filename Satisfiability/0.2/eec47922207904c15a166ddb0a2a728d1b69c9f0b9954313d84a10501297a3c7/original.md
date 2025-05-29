```
reset_assertions!(solver::InteractiveSolver)
```

Removes all assertions, popping n levels off the solver's assertion stack. After this command, the stack will be at level 1 and there will be no assertions set. See [section 4.2.1](http://smtlib.cs.uiowa.edu/papers/smt-lib-reference-v2.6-r2021-05-12.pdf) of the SMT-LIB standard.
