```
 write_json(df::DataFrame, path::String;JSONObjectVector::Bool=true)

 DataFrameの内容を指定されたJSONファイルに書き込みます
```

# 引数

  * `df::DataFrame`: JSONファイルに書き込むデータを含むDataFrame
  * `path::String`: 書き込むローカルJSONファイルのパス
  * `JSONObjectVector::Bool`: 書き込むJSONフォーマットを決定します。trueはJSONオブジェクトのベクターとして書き込むことを意味し、falseはJSON配列として書き込みます

# 例

```
julia> df = DataFrame(A=1:5, B=["a", missing, "c", "d", "e"], C=[1.1, 2.2, 3.3, 4.4, 5.5]);

julia> write_json(df, "data.json")
```
