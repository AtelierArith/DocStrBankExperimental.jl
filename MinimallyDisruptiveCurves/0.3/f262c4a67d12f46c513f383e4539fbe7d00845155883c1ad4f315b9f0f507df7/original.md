```
(c::MDCProblem)()
```

returns a tuple of ODEProblems specificed by the MDCProblem. Usually a single ODEProblem. Two are provided if the curve crosses zero, so that one can run two curves in parallel going backwards/forwards from zero
