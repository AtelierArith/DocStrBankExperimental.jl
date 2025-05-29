```
JuMP.add_constraint(graph::OptiGraph, con::JuMP.AbstractConstraint, name::String="")
```

`graph`に新しい制約を追加します。このメソッドは、ユーザーがJuMP.@constraintマクロを使用したときに内部的に呼び出されます。
