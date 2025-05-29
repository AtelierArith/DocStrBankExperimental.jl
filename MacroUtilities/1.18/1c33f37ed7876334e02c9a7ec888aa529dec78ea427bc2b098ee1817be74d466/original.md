```
FuncArg(; name, type, value::Any, is_splat::Bool)
```

Matches a function argument expression

# Fields

  * `name::Union{NotProvided, Symbol} = not_provided`: Name of the argument
  * `type::Union{NotProvided, Symbol, Expr} = not_provided`: Annotated type of the argument. Only valid when `value` is not provided.
  * `value::Any = not_provided`: Value of the argument. If `name` is provided, this corresponds to the default value of `name` in a method definition. Otherwise, this is the value passed as a function argument
  * `is_splat::Bool = false`: `true` if this argument is splatted, `false` otherwise
