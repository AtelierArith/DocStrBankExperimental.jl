```
Dataset(dataset_name=str::String; kwargs...)
```

An object that stores configuration, and file path locations. Assertions constrain valid field values. If `rundate` is not the current date, the `latest_path` will not be used.

*NOTE:* No positional arguments allowed b/c of @kw_def, keyworded args only.

Supported keyword arguments (default show first):

```
dataset_name::String (required)
datastore_type ∈ ["local", "remote"]
dataset_type ∈ ["extracts", "reports", "images"]
file_format ∈ ["csv"]
rundate::Date = Datest.today()
rundate_type ∈ ["latest", "specific"]
```

Read/write behavior depends on rundate/rundate_type combination as follows:

```
rundate_type|  rundate   || read    |  write
------------|------------||---------|-----------------------------------------
latest      |  == today  || latest  |  [latest, rundate]   default option
latest      |  != today  || latest  |  [latest]            dont write to date partition (rare)
specific    |  == today  || rundate |  [rundate]
specific    |  != today  || rundate |  [rundate]
```

# Examples

```julia
julia> begin
    ENV["PREFECT_DATA_BLOCK_LOCAL"] = "local-file-system/willowdata"
    ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api"
end;

julia> ds = Dataset(dataset_name="test_table", datastore_type="local")
Dataset
  dataset_name: String "test_table"
  datastore_type: String "local"
  dataset_type: String "extracts"
  file_format: String "csv"
  rundate: Dates.Date
  rundate_type: String "latest"
  dataset_path: String "extracts/csv/dataset=test_table/rundate=2023-07-24/data.csv"
  latest_path: String "extracts/csv/latest/dataset=test_table/data.csv"
  image_path: String "extracts/dataset=test_table/rundate=2023-07-24"

julia> df = read(ds)
1×2 DataFrame
 Row │ column1                            result
     │ String                             String7
─────┼────────────────────────────────────────────
   1 │ If you can select this table you…  PASSED
```
