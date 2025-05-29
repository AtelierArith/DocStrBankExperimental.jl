```
create_introspected_struct([client::Client], object_name::AbstractString, fields::AbstractDict)
```

指定されたオブジェクトの構造体を作成し、`fields`のキーと値でそのフィールドを埋めます。

# 例

```julia
julia> GraphQLClient.create_introspected_struct("ResultObject",Dict(:resultId=>"MyResult", :Score => 1.0))
ResultObject
  Score : 1.0
      resultId : MyResult
```
