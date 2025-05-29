```
signin(db::Surreal; user::String, pass::String)::Union{String, Nothing}
```

この接続を特定の認証スコープにサインインします。

# 引数

  * `user`: サインインクエリのユーザー名
  * `pass`: サインインクエリのパスワード

# 例:

```jldoctest
julia> signin(db, user="root", pass="root")
```
