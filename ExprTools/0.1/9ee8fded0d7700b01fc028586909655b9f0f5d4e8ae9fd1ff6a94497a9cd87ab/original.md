```
signature(m::Method) -> Dict{Symbol,Any}
```

Finds the expression for a method's signature as broken up into its various components including:

  * `:name`: Name of the function
  * `:params`: Parametric types defined on constructors
  * `:args`: Positional arguments of the function
  * `:whereparams`: Where parameters

All components listed above may not be present in the returned dictionary if they are not in the function definition.

Limited support for:

  * `:kwargs`: Keyword arguments of the function. Only the names will be included, not the default values or type constraints.

Unsupported:

  * `:rtype`: Return type of the function
  * `:body`: Function body0
  * `:head`: Expression head of the function definition (`:function`, `:(=)`, `:(->)`)

For more complete coverage, consider using [`splitdef`](@ref) with [`CodeTracking.definition`](https://github.com/timholy/CodeTracking.jl).

The dictionary of components returned by `signature` match those returned by [`splitdef`](@ref) and include all that are required by [`combinedef`](@ref), except for the `:body` component.

# keywords

  * `extra_hygiene=false`: if set to `true` this forces name-hygiene on the `TypeVar`s in  `UnionAll`s, regenerating each with a unique name via `gensym`. This shouldn't actually be required as they are scoped such that they are not supposed to leak. However, there is a long-standing [julia bug](https://github.com/JuliaLang/julia/issues/39876) that means  they do leak if they clash with function type-vars.
