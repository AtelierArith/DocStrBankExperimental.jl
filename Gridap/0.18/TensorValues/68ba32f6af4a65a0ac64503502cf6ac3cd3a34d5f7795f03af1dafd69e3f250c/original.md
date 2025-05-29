```
num_indep_components(::Type{<:Number})
num_indep_components(a::Number)
```

Number of independant components of a `Number`, that is `num_components` minus the number of components determined from others by symmetries or constraints.

For example, a `TensorValue{3,3}` has 9 independant components, a `SymTensorValue{3}` has 6 and a `SymTracelessTensorValue{3}` has 5. But they all have 9 (non independant) components.
