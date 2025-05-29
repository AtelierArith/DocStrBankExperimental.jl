```
read_single_record(ds::MetopDataset, record_type::Type{<:Record})
read_single_record(file_pointer::IO, record_type::Type{<:Record})
read_single_record(file_path::AbstractString, record_type::Type{<:Record})
```

Read the n'th record of type `record_type` from the dataset. This can be used to access records that are  not directly exposed through the `MetopDataset` interface.
