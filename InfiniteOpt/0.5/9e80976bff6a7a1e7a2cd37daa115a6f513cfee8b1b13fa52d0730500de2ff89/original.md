```
GeneralVariableRef <: JuMP.AbstractVariableRef
```

A `DataType` that serves as the principal variable reference in `InfiniteOpt` for building variable expressions. It contains the needed information to create a variable type specifc reference (e.g., [`InfiniteVariableRef`](@ref)) via [`dispatch_variable_ref`](@ref) to obtain the correct subtype of [`DispatchVariableRef`](@ref) based off of `index_type`. This allows us to construct expressions using concrete containers unlike previous versions of `InfiniteOpt` which provides us a significant performance boost.

**Fields**

  * `model::InfiniteModel`: Infinite model.
  * `raw_index::Int64`: The raw index to be used in the `index_type` constructor.
  * `index_type::DataType`: The concrete [`AbstractInfOptIndex`](@ref) type/constructor.
  * `param_index::Int`: The index of a parameter in [`DependentParameters`](@ref). This is ignored for other variable types.
