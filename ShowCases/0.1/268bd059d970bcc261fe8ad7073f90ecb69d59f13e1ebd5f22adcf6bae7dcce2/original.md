```
ShowKw(o, name, separator=Print("="); kw...)
ShowKw(o, name::Symbol, separator=Print("="); kw...)
```

Show an object as if it were a keyword argument with name `name`.  For example `ShowKw(x, :x)` shows `x=x`.

## Constructors

  * `o`: the object to be wrapped.
  * `name`: The name of the object, if a `Symbol` will be printed as in keyword arguments.
  * `separator`: separator between the name and shown object.
  * `kw`: Keyword arguments passed to [`ShowList`](@ref).
