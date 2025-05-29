```
AbstractRuntimeOptions
```

An abstract type representing runtime configuration parameters for the symbolic regression algorithm.

`AbstractRuntimeOptions` is used by `equation_search` to control runtime aspects such as parallelism and iteration limits. By subtyping `AbstractRuntimeOptions`, advanced users can customize runtime behaviors by passing it to `equation_search`.

# See Also

  * [`RuntimeOptions`](@ref): Default implementation used by `equation_search`.
  * [`equation_search`](@ref SymbolicRegression.equation_search): Main function to perform symbolic regression.
  * [`AbstractOptions`](@ref SymbolicRegression.CoreModule.OptionsStruct.AbstractOptions): See how to extend abstract types for customizing options.
