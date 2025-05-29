```
struct StorCapOpexFixed <: AbstractStorageParameters
```

A storage parameter type for including a capacity and fixed operational expenditures. This implies that the installed capacity has no direct impact on the objective function.

# Fields

  * **`capacity::TimeProfile`** is the installed capacity.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity through the variable `:cap_inst`.
