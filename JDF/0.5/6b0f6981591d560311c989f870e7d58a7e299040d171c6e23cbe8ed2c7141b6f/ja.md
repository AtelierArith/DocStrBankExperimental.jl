```
JDF.names(indir)
```

`indir`に関連付けられたJDFの列名をロードします。

# 例

```julia
using JDF, DataFrames
JDF.save(DataFrame(a = 1:3, b = 1:3), "plsdel.jdf")
JDF.names("plsdel.jdf")
```
