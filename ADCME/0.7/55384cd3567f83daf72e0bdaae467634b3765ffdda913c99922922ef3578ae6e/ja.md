```
load(sess::PyObject, file::String, vars::Union{PyObject, Nothing, Array{PyObject}}=nothing, args...; kwargs...)
```

セッション`sess`にファイル`file`から変数の値をロードします。`vars`がnothingの場合、すべての学習可能な変数に値をロードします。詳細は[`save`](@ref)、[`load`](@ref)を参照してください。
