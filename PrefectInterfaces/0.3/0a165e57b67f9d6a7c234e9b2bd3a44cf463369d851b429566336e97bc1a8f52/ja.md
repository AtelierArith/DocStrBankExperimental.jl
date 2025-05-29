```
LocalFSBlock(blockname::String, blocktype::String, basepath::String)
```

PrefectのLocalFileSystemブロックに対応しています。添付された関数：

```
read_path("path/to/file.csv")
write_path("path/to/file.csv", df::AbstractDataFrame)
```

"LocalFSBlock.basepath/path/to/file.csv"にDataFrameファイルを返すか、書き込みます。

# 例：

```julia
julia> fsblock = PrefectBlock("local-file-system/willowdata");

julia> df = fsblock.block.read_path("extracts/csv/dataset=test_table/rundate=2023-05-25/data.csv")
1×2 DataFrame
 Row │ column1                            result
     │ String                             String7
─────┼────────────────────────────────────────────
   1 │ If you can select this table you…  PASSED

```
