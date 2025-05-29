```
dispatch_variable_ref(vef::GeneralVariableRef)::DispatchVariableRef
```

Return the concrete [`DispatchVariableRef`](@ref) this associated with `vref`. This relies on `dispatch_variable_ref` being extended for the index type, otherwise an `MethodError` is thrown.
