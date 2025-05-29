```
Surreal(url::Union{Nothing, String}, token::Union{Nothing, String}, client_state::ConnectionState, ws::Union{Nothing, websocket}
```

A struct represents a Surreal server.

# Constructors

```julia
Surreal()
Surreal(url::String)
```

# Keyword arguments

  * url: The URL of the Surreal server.

# Examples

```jldoctest
db = Surreal("ws://127.0.0.1:8000/rpc")
db = Surreal("http://cloud.surrealdb.com/rpc")
```
