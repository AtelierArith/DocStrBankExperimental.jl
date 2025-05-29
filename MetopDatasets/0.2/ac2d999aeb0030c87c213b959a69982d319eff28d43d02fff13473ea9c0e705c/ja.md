```
read_single_record(ds::MetopDataset, record_type::Type{<:Record})
read_single_record(file_pointer::IO, record_type::Type{<:Record})
read_single_record(file_path::AbstractString, record_type::Type{<:Record})
```

データセットからタイプ `record_type` の n 番目のレコードを読み取ります。これは、`MetopDataset` インターフェースを通じて直接公開されていないレコードにアクセスするために使用できます。
