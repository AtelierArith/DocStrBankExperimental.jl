```
authenticate(db::Surreal; token::Union{String, Nothing}=nothing)::Nothing
```

現在の接続をJWTトークンで認証します。

# 引数

  * `token`: 接続に使用するトークン。

# 例

```jldoctest
julia> authenticate(db, token="JWT token here")
```
