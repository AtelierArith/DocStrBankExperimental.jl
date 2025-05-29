```
relax_integrality(stochasticprogram::StochasticProgram)
```

Modifies `stochasticprogram` to "relax" all binary and integrality constraints on decisions and auxiliary variables.

Returns a function that can be called without any arguments to restore the original stochasticprogram. The behavior of this function is undefined if additional changes are made to the affected decisions and variables in the meantime.
