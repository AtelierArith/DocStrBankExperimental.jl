```
computed_properties_with_inputs(s::Subsystem)
```

Signal that a subsystem has properties which can be computed on-the-fly based on it's existing properties. In the termoinology used by ModelingToolkit.jl, these are "observed states", but they also require the inputs to the subsystem to compute (and thus are non-local to the subsystem).

This function takes in a `Subsystem` and returns a `NamedTuple` where each key is a property name that can be computed, and each value is a function that takes in the subsystem and returns a computed value.

By default, this function returns an empty NamedTuple.

This is typically only usable on objects like ODESolutions.
