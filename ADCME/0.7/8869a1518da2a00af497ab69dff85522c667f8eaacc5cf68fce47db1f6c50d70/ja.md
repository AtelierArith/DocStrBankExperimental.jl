```
save(sess::PyObject, file::String, vars::Union{PyObject, Nothing, Array{PyObject}}=nothing, args...; kwargs...)
```

`sess`のセッション内の`vars`の値を保存します。結果は`file`に辞書として書き込まれます。`vars`がnothingの場合、すべての学習可能な変数が保存されます。詳細は[`save`](@ref)、[`load`](@ref)を参照してください。
