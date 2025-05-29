```
colmetadata(x, [col]; style::Bool=false)
```

If `col` is not passed return a dictionary mapping columns represented as `Symbol` that have associated metadata to dictionaries mapping all metadata keys to metadata values associated with table `x` for a given column.

If `col` is passed return a dictionary mapping all column metadata keys to metadata values associated with column `col` of table `x`. Throw an error if `x` does not support reading metadata for column `col` or column `col` is not present in `x`.

If `style=true` values are tuples of metadata value and metadata style. Metadata style is an additional information about the kind of metadata that is stored for the `key`.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.

The returned dictionary may be freshly allocated on each call to `colmetadata` and is considered to be owned by `x` so it must not be modified.
