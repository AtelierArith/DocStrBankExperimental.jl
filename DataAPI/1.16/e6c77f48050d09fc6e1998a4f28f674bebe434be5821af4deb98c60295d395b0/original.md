```
metadata!(x, key::AbstractString, value; style::Symbol=:default)
```

Set metadata for object `x` for key `key` to have value `value` and style `style` (`:default` by default) and return `x`. Throw an error if `x` does not support setting metadata.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.
