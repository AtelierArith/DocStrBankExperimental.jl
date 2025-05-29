```
name_to_function(model::InfiniteModel, name::Symbol, num_args::Int)::Union{Function, Nothing}
```

`name`に対応する登録された関数を`num_args`と共に返します。登録された関数が存在しない場合は`nothing`を返します。これは、`NLPExpr`に格納された関数名の関数を取得するのに役立ちます。
