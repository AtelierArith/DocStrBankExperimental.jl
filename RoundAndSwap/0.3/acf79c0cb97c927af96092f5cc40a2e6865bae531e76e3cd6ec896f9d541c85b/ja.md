```
make_models(model::Model, optimizer::Union{Nothing, DataType} = nothing)
```

単一のモデルを与えられた場合、各スレッド用に十分なモデルを作成します

# 引数:

  * `optimizer`: 使用するオプティマイザ。何も指定しない場合は、提供されたモデルのものと同じものを使用します。これは[Gurobi, Ipopt, HiGHS]のいずれかである必要があります。
