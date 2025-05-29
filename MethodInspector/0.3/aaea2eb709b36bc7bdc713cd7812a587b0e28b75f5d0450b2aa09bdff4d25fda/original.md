  * `kwarg_types(::Method)` → `Type[]`

Given a Method, return a list of types of the keyword warguments supported by that method.

### Arguments

`m::Method` : The method to check for `kwargs`

### Returns

A `Type` array of the kwarg types supported by method `m`. Arg names can be fetched using [`kwarg_names`](@ref). Both functions will return values in the same order. Methods that do not support `kwargs` will return an empty array.

### Examples

```julia
kwarg_types(foo)
```
