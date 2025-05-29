```
JuMP.set_start_value(
    graph::OptiGraph, 
    nvref::NodeVariableRef, 
    value::Union{Nothing,Real}
)
```

変数 `nvref` の開始値を `graph` に設定します。異なるグラフは、ノード変数に対して異なる開始値を持つことがあることに注意してください。
