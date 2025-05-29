```
abstract type MultipleMinBudgetedSolution
```

A type of `MinBudgetedSolution` when several solutions are available, with  the several values of the budget that are specified by the combinatorial  instance (typically, from zero to a maximum value). 

Objects of this type have to implement the usual fields of  `CombinatorialSolution`, but also `solutions`, a mapping from a budget value to the corresponding solution (`solutions`[i]`corresponds to a minimum budget of`i`).
