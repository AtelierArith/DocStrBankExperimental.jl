```
metastyle(tb::ReadStatTable, [key::Union{Symbol, AbstractString}])
```

Return the specified style(s) of all metadata for table `tb`. If a metadata `key` is specified, only the style for the associated metadata are returned. By default, metadata on labels and notes have the `:note` style; all other metadata have the `:default` style.

The style of metadata is only determined by `key` and hence is not distinguished across different columns.
