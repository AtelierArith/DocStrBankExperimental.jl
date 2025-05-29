```
fun(obj::T)
fun(obj::Symbol)
```

Prints a comprehensive list of functions that can be called on `obj`, both `exported` and `unexported`. Note that `T` can only be a Julia stdlib type or a composite type that is a subtype of a Julia stdlib type. If a type that does not meet these requirements is used, an error will be thrown.

Only un`exported` functions with docstrings are included, as there is a chance they may be added to the public API. To access these unexported functions, one would typically use the qualified name, such as `Base.«function»`, or the package name in use in place of `Base`, to access these un`exported` functions.

Examples of using `fun` can be found in the docstrings of `REPLference`, using the `help?>` mode.
