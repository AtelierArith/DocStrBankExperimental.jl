```
dict2colmetadata!(table, dict; style::Bool=false, defaultstyle::Symbol=:default)
```

Store column-level metadata stored in `dict` in `table` (discarding all previously present column-level metadata).

`style` keyword argument indicates if `dict` has style information (`false` by default). If `style` is `false` then `defaultstyle` (`:default` by default) is used when setting metadata style. If style is passed it can be any value, but it will be converted to `Symbol` internally.

The funcion assumes that `dict` stores key-value pairs, where key is column name and value are dictionaries storing metadata key-value pairs; it is typically previously generated by the `colmetadata` function.

See also: [`dict2metadata!`](@ref)
