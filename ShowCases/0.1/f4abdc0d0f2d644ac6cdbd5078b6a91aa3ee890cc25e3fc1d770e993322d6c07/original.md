```
ShowTypeOf(o, type_style=Style(), show_module=:context, show_params=true, kw...)
```

Show the type of object `o`.

## Arguments

  * `type_style::Style`: Style to use for the type.
  * `show_module::Symbol`: whether to show modules for the type and its parameters.  See [`ShowType`](@ref) for options.
  * `kw`: All other keyword arguments passed to [`ShowParams`](@ref)
