```
logging(file::Union{Nothing,String}, o::PyObject...; summarize::Int64 = 3, sep::String = " ")
```

`o`を`file`にログ記録します。この演算子は[`bind`](@ref)と一緒に使用する必要があります。
