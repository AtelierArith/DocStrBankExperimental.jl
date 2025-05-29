```
Dataset(dataset_name=str::String; kwargs...)
```

設定とファイルパスの場所を保存するオブジェクトです。アサーションは有効なフィールド値を制約します。`rundate`が現在の日付でない場合、`latest_path`は使用されません。

*注意:* @kw_defのため位置引数は許可されず、キーワード引数のみです。

サポートされているキーワード引数（デフォルトは最初に表示）:

```
dataset_name::String (必須)
datastore_type ∈ ["local", "remote"]
dataset_type ∈ ["extracts", "reports", "images"]
file_format ∈ ["csv"]
rundate::Date = Datest.today()
rundate_type ∈ ["latest", "specific"]
```

読み書きの動作は、rundate/rundate_typeの組み合わせに依存します:

```
rundate_type|  rundate   || read    |  write
------------|------------||---------|-----------------------------------------
latest      |  == today  || latest  |  [latest, rundate]   デフォルトオプション
latest      |  != today  || latest  |  [latest]            日付パーティションに書き込まない（稀）
specific    |  == today  || rundate |  [rundate]
specific    |  != today  || rundate |  [rundate]
```

# 例

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
   1 │ このテーブルを選択できる場合…  PASSED
```
