```
signup(db::Surreal; user::String, pass::String)::Union{String, Nothing}
この接続を特定の認証スコープにサインアップします。
```

#引数

  * `user`: サインアップクエリのユーザー名
  * `pass`: サインアップクエリのパスワード

# 例

```jldoctest
julia> signup(db, user="bob", pass="123456")
```
