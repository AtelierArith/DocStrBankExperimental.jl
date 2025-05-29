```
metastyle!(tb::ReadStatTable, key::Union{Symbol, AbstractString}, style::Symbol)
```

Set the style of all metadata associated with `key` to `style` for table `tb`.

The style of metadata is only determined by `key` and hence is not distinguished across different columns.
