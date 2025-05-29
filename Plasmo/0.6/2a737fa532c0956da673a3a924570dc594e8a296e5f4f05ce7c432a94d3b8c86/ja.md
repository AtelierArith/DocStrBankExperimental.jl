```
JuMP.num_constraints(graph::OptiGraph; count_variable_in_set_constraints=true)
```

`graph`内の制約の総数を返します。`count_variable_in_set_constraints`がtrueに設定されている場合、変数の境界制約も含まれます。
