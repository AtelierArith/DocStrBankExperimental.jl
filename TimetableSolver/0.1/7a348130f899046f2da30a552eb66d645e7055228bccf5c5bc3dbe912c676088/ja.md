```
get_model(vardata::VariableData, timeout::Float64=Inf, all_solutions::Bool=false)::Tuple{Model,OrderedDict}
```

`vardata`を使用して作成されたJuMPモデルと、モデルで定義された変数のOrderedDictを返します。

# 引数

  * `vardata::VariableData`: モデルに追加される変数と制約を表すVariableDataオブジェクト。
  * `timeout::Float64=Inf`: モデルを実行する最大時間を表すFloat。
  * `all_solutions::Bool=false`: すべての解を返すか、最初の解のみを返すかを表すBool。

# 注意事項

  * 正しい変数を持つモデルを作成し、モデルに制約を追加します。
  * 定義された変数は匿名であるため、それらは整数表現にマッピングされたOrderedDictに格納されます。
