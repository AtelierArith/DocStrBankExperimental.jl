  * `kwarg_names(::Method)` → `Symbol[]`

Given a method, return the names of all Keyword Arguments of that method.

### Arguments

`m::Method` : The method to check for `kwargs`

### Returns

A `Symbol` array of the kwargs supported by method `m`. Arg types can be fetched using [`kwarg_types`](@ref) which returns types in the same order. Default values are not returned. Methods that do not support `kwargs` will return an empty array.

### Examples

```julia
kwarg_names(methods(foo).ms[1])

kwarg_names(methods(foo, (Int,), MyModule))
```
