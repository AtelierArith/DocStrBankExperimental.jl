```
Surreal(url::Union{Nothing, String}, token::Union{Nothing, String}, client_state::ConnectionState, ws::Union{Nothing, websocket}
```

構造体はSurrealサーバーを表します。

# コンストラクタ

```julia
Surreal()
Surreal(url::String)
```

# キーワード引数

  * url: SurrealサーバーのURL。

# 例

```jldoctest
db = Surreal("ws://127.0.0.1:8000/rpc")
db = Surreal("http://cloud.surrealdb.com/rpc")
```
