```
solvector([;state=][,constraint=][,aux_state=])
```

Build a solution vector for a constrained system. This takes three optional keyword arguments: `state`, `constraint`, and `aux_state`. If only a state is supplied, then the constraint is set to an empty vector and the system is assumed to correspond to an unconstrained system. (`aux_state` is ignored in this situation.)
