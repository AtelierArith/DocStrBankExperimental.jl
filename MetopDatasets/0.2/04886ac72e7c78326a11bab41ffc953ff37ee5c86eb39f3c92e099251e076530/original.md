```
MetopDiskArray(file_pointer::IOStream,
    record_layouts::Vector{FixedRecordLayout},
    field_name::Symbol; auto_convert = true) -> MetopDiskArray
```

Constructor for MetopDiskArray that compute additional fields. `auto_convert = true` will automatically convert custom `RecordSubType` to commonly used data types e.g. converting `VInteger` to `Float64`.
