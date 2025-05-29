```
colmetadata(x, col, key::AbstractString, [default]; style::Bool=false)
```

Return metadata value associated with table `x` for column `col` and key `key`. Throw an error if `x` does not support reading metadata for column `col` or `x` supports reading metadata, but does not have a mapping for column `col` for `key`.

`col` must have a type that is supported by table `x` for column indexing. Following the Tables.jl contract `Symbol` and `Int` are always allowed. Throw an error if `col` is not a column of `x`.

If `style=true` return a tuple of metadata value and metadata style. Metadata style is an additional information about the kind of metadata that is stored for the `key`.

One of the uses of the metadata `style` is decision how the metadata should be propagated when `x` is transformed. This interface defines the `:default` style that indicates that metadata should not be propagated under any operations (it is only preserved when a copy of the source table is performed). All types supporting metadata allow at least this style.

If `default` is passed then return it if `x` supports reading metadata and has column `col` but mapping for `key` is missing. If `style=true` return `(default, :default)`.
