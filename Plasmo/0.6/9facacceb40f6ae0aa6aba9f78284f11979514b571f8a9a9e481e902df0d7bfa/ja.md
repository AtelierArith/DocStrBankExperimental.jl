```
JuMP.dual(graph::OptiGraph, cref::EdgeConstraintRef; result::Int=1)
```

`cref` の双対値を `graph` で返します。この値は `graph` に対する最適化ソリューションに特有であることに注意してください。`cref` は、それが含まれる異なるオプティグラフに対して異なる値を持つことがあります。
