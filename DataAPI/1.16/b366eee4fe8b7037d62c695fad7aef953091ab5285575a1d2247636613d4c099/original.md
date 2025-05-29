```
metadata(x, key::AbstractString, [default]; style::Bool=false)
```

Return metadata value associated with object `x` for key `key`. Throw an error if `x` does not support reading metadata or does not have a mapping for `key`.

If `style=true` return a tuple of metadata value and metadata style. Metadata style is an additional information about the kind of metadata that is stored for the `key`.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.

If `default` is passed then return it if reading metadata is supported but mapping for `key` is missing. If `style=true` return `(default, :default)`.
