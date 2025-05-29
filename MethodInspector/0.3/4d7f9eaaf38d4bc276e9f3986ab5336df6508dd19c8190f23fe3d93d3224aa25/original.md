  * `arg_names(::Method)` → `Symbol[]`

Given a method, return a list of args required by that method.

### Arguments

`m::Method` : The Method or MethodList to check for `args`

#### Returns

A `Symbol` array of the args required by the first method passed in. Arg types and default values are not returned.  Functions with no required `args` will return an empty array.

### Examples

```julia
arg_names(foo)
```
