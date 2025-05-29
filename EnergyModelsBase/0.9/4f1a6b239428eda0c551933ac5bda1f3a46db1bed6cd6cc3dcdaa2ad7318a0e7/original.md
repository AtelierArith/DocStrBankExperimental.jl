```
struct StorOpexVar <: AbstractStorageParameters
```

A storage parameter type for including variable operational expenditures. This implies that the charge or discharge rate do not have a capacity and the [`Storage`](@ref) level can be used within a single `TimePeriod`.

This type can only be used for the fields `charge` and `discharge`.

# Fields

  * **`opex_var::TimeProfile`** is the variable operating expense per capacity usage through the variable `:cap_use`.
