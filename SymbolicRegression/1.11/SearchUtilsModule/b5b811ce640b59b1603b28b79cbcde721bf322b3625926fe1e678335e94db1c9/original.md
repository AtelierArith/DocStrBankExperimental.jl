```
AbstractSearchState{T,L,N}
```

An abstract type encapsulating the internal state of the search process during symbolic regression.

`AbstractSearchState` instances hold information like populations and progress metrics, used internally by `equation_search`. Subtyping `AbstractSearchState` allows customization of search state management.

Look through the source of `equation_search` to see how this is used.

# See Also

  * [`SearchState`](@ref): Default implementation of `AbstractSearchState`.
  * [`equation_search`](@ref SymbolicRegression.equation_search): Function where `AbstractSearchState` is utilized.
  * [`AbstractOptions`](@ref SymbolicRegression.CoreModule.OptionsStruct.AbstractOptions): See how to extend abstract types for customizing options.
