```
read(ds::Dataset)
```

Returns a `DataFrame` by calling `CSV.read` on a filepath defined by the Dataset type.

*NOTE:* A prefect server must be available to use Dataset read function.

# Examples

```julia
julia> begin
    ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api"
    ENV["PREFECT_DATA_BLOCK_LOCAL"] = "local-file-system/willowdata"
end;

julia> df = read(Dataset(dataset_name="test_table", datastore_type="local"))
1×2 DataFrame
 Row │ column1                            result
     │ String                             String7
─────┼────────────────────────────────────────────
   1 │ If you can select this table you…  PASSED
```
