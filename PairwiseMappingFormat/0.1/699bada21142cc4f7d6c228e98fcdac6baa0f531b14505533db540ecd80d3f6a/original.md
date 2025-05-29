```
is_mapped(x::PAFRecord) -> Bool
```

Compute whether the `PAFRecord` is mapped. An unmapped record will have the properties `is_rc` and `tname` unavailable. The properties `qname` and `qlen`, and the auxiliary data of an unmapped record can be relied on, but the remaining properties contain arbitrary data. Note that some PAF parsers do not handle unmapped records correctly, so be wary when writing unmapped records.

# Examples

```jldoctes
julia> is_mapped(record)
true
```

See also: [`PAFRecord`](@ref)
