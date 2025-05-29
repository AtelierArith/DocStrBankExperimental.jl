```
record_struct_expression(file_name, record_type)
```

CSVファイルに基づいて`Struct`コードを自動生成する関数です。また、`Struct`のために`get_description`と`get_scale_factor`メソッドも自動生成します。`eval`と一緒に使用してください。

# 例

```julia-repl
julia> eval(record_struct_expression(joinpath(@__DIR__, "TEST_FORmaT.csv"), DataRecord))
julia> TEST_FORMAT <: DataRecord
true
```
