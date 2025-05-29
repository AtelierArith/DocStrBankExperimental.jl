```
DiscreteInvestment <: Investment
```

Discrete investment with integer variables using an increment. The increment for the discrete investment can be different for the individual strategic periods.

Discrete investments introduce one integer variable for each investment period.

# Fields

  * **`increment::TimeProfile`** is the used increment.
