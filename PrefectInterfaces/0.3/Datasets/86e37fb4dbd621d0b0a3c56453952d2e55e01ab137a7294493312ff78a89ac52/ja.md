```
read(ds::Dataset)
```

`Dataset`型によって定義されたファイルパスに対して`CSV.read`を呼び出すことで`DataFrame`を返します。

*注意:* Datasetの読み取り関数を使用するには、完璧なサーバーが利用可能でなければなりません。

# 例

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
