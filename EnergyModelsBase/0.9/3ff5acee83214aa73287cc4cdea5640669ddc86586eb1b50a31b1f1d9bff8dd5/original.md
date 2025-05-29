```
struct StorCapOpexVar <: AbstractStorageParameters
```

A storage parameter type for including a capacity and variable operational expenditures. This implies that the installed capacity has no direct impact on the objective function.

# Fields

  * **`capacity::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per capacity usage through the variable `:cap_use`.
