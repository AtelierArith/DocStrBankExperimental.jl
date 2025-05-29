```
LocalFSBlock(blockname::String, blocktype::String, basepath::String)
```

Corresponds with the Prefect LocalFileSystem block. Attached functions:

```
read_path("path/to/file.csv")
write_path("path/to/file.csv", df::AbstractDataFrame)
```

Returns or writes a DataFrame file at "LocalFSBlock.basepath/path/to/file.csv".

# Examples:

```julia
julia> fsblock = PrefectBlock("local-file-system/willowdata");

julia> df = fsblock.block.read_path("extracts/csv/dataset=test_table/rundate=2023-05-25/data.csv")
1×2 DataFrame
 Row │ column1                            result
     │ String                             String7
─────┼────────────────────────────────────────────
   1 │ If you can select this table you…  PASSED

```
