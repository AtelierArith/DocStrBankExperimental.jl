```
JuMP.dual(graph::OptiGraph, cref::NodeConstraintRef; result::Int=1)
```

`graph`内の`cref`の双対値を返します。この値は`graph`に対する最適化ソリューションに特有であることに注意してください。`cref`は、それが含まれる異なるオプティグラフに対して異なる値を持つ可能性があります。
