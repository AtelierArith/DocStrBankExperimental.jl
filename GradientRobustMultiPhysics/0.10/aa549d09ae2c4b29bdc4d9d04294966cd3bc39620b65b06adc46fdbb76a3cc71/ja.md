```
function DataFunction(c::Array{<:Real,1}; name = "constant user data", quadorder::Int = 0)
```

与えられた配列 c から直接 DataFunction を生成します。すなわち、x や t に依存しない定数の DataFunction です。
