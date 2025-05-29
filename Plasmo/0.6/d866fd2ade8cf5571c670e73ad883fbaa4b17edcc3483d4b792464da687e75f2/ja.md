```
JuMP.set_objective(
    graph::OptiGraph, 
    sense::MOI.OptimizationSense, 
    func::JuMP.AbstractJuMPScalar
)
```

`graph`の目的関数と目的感を設定します。このメソッドは、ユーザーが`JuMP.@objective`マクロを使用したときに内部的に呼び出されます。
