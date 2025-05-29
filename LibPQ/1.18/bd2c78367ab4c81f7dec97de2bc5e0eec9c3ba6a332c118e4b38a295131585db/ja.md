```
status(jl_conn::Connection) -> libpq_c.ConnStatusType
```

PostgreSQLデータベース接続の状態をlibpqに従って返します。ブロッキング接続に対しては`CONNECTION_OK`と`CONNECTION_BAD`のみが有効であり、現在サポートされているのはブロッキング接続のみです。

参照: [`error_message`](@ref)
