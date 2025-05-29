```julia
struct RegistryError <: Exception
```

Exception raised, if a certain type `target_type` can not be registed for a certain interface, since there needs the function `func` to be impleemnted.

# Fields

  * `func::Function`
  * `target_type::Any`
