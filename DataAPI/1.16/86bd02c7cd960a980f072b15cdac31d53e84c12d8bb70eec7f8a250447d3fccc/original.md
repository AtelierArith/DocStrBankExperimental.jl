```
colmetadata!(x, col, key::AbstractString, value; style::Symbol=:default)
```

Set metadata for table `x` for column `col` for key `key` to have value `value` and style `style` (`:default` by default) and return `x`. Throw an error if `x` does not support setting metadata for column `col`.

`col` must have a type that is supported by table `x` for column indexing. Following the Tables.jl contract `Symbol` and `Int` are always allowed. Throw an error if `col` is not a column of `x`.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.
