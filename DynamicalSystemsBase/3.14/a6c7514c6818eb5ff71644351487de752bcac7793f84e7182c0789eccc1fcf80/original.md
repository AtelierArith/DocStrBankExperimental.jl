```
set_parameter!(ds::DynamicalSystem, index, value [, p])
```

Change a parameter of `ds` given the `index` it has in the parameter container and the `value` to set it to. This function works for any type of parameter container (array/dictionary/composite types) provided the `index` is appropriate type.

The `index` can be a traditional Julia index (integer for arrays, key for dictionaries, or symbol for composite types). It can also be a symbolic variable or `Symbol` instance. This is valid only for dynamical systems referring a ModelingToolkit.jl model which also has `index` as one of its parameters.

The last optional argument `p` defaults to [`current_parameters`](@ref) and is the parameter container whose value is changed at the given index. It must match layout with its default value.
