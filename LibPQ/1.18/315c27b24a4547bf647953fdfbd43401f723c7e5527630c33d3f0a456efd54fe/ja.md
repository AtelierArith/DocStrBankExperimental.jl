```
execute(jl_conn::Connection, copyin::CopyIn, args...;
    throw_error::Bool=true, kwargs...
) -> Result
```

`copyin`のクエリで[`execute`](@ref execute(::Connection, ::String))を実行し、その後`copyin`のデータをサーバーに送信します。

他のすべての引数は、初期クエリの`execute`呼び出しに渡されます。
