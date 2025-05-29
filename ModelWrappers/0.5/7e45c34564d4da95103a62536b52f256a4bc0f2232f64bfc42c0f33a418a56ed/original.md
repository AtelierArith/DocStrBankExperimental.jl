```julia
struct Param{A, B}
```

Utility struct to define Parameter in a way ModelWrappers.jl can handle. Will be separated in ModelWrapper struct for type stability.

# Fields

  * `constraint::Any`
  * `val::Any`
