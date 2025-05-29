```
struct StorCapOpex <: AbstractStorageParameters
```

A storage parameter type for including a capacity as well as variable and fixed operational expenditures.

# Fields

  * **`capacity::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per capacity usage through the variable `:cap_use`.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity through the variable `:cap_inst`.
