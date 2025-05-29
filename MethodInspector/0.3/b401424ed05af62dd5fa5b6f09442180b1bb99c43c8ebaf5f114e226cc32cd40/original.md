  * `arg_types(::Method)` → `Type[]`

Given a method, return the datatype of all its positional arguments.

### Arguments

`m::Method` : The Method or MethodList to check for `args`

### Returns

A `Type` array of the arg types supported by method `m`. Arg names can be fetched using [`arg_names`](@ref). Both functions will return values in the same order. Methods that do not support `args` will return an empty array.

### Examples

```julia
arg_types(foo)
```
