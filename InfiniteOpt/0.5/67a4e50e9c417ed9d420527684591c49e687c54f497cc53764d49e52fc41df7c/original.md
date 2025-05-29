```
DependentParameterIndex <: AbstractInfOptIndex
```

A `DataType` for storing the index of an indiviudal parameter in a [`DependentParameters`](@ref) object.

**Fields**

  * `object_index::DependentParametersIndex`: The index of the parameter collection.
  * `param_index::Int`: The index of the individual parameter in the above object.
