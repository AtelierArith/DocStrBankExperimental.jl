```
metadata(x; style::Bool=false)
```

Return a dictionary mapping all metadata keys to metadata values associated with object `x`. Throw an error if `x` does not support reading metadata.

If `style=true` values are tuples of metadata value and metadata style. Metadata style is an additional information about the kind of metadata that is stored for the `key`.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.

The returned dictionary may be freshly allocated on each call to `metadata` and is considered to be owned by `x` so it must not be modified.
