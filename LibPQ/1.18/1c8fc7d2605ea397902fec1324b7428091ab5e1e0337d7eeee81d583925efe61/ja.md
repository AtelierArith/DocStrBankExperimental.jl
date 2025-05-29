```
reset!(jl_conn::Connection; throw_error=true)
```

PostgreSQLサーバーへの通信をリセットします。`PGconn`オブジェクトは、同一の接続パラメータを使用して再作成されます。

`throw_error`引数に関する情報は、[`handle_new_connection`](@ref)を参照してください。

!!! note
    この関数は、例えば`CONNECTION_BAD`の状態の接続で呼び出すことができますが、閉じられた接続では呼び出すことはできません。

