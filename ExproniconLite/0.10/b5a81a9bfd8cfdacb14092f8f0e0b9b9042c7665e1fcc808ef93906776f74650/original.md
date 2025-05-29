```
JLCall(func, args::Vector, kwargs::Maybe{Vector})
JLCall(; func, args=[], kwargs=nothing)
```

Represents a Julia function call expression.

# Fields and Keyword Arguments

All the following fields are valid as keyword arguments `kw` in the constructor, and can be access via `<object>.<field>`.

  * `func`: the function being called
  * `args`: optional, function arguments, a list of `Expr` or `Symbol`.
  * `kwargs`: optional, function keyword arguments, a list of `Expr(:kw, name, default)`.
