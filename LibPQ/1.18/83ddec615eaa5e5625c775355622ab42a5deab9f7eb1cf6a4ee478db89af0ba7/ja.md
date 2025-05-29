```
prepare(jl_conn::Connection, query::AbstractString) -> Statement
```

PostgreSQLサーバー上でlibpqを使用して準備されたステートメントを作成します。ステートメントには、[`unique_id`](@ref)を使用して生成された一意の名前が付けられます。

!!! note
    現在、ステートメントは明示的に解放されませんが、[DEALLOCATEに関するPostgreSQLのドキュメント](https://www.postgresql.org/docs/10/sql-deallocate.html)に従って、セッションの終了時に解放されます。

