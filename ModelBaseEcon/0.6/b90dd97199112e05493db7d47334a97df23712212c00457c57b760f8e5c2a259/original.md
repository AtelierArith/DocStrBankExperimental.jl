```
findequations(m::Model, sym::Symbol; verbose=true)
```

Prints the equations which use the the given symbol in the provided model and returns a vector with their keys. Only returns the vector if verbose is set to `false`.
