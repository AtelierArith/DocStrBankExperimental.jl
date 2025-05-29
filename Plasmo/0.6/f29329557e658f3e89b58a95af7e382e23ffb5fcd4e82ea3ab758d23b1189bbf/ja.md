```
JuMP.value(graph::OptiGraph, nvref::NodeVariableRef; result::Int=1)
```

`nvref`の原始値を`graph`内で返します。この値は`graph`に対する最適化ソリューションに特有であることに注意してください。`nvref`は、それが含まれる異なるオプティグラフに対して異なる値を持つことがあります。
