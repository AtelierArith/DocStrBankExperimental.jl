```
get_cookie(
    payload::Union{HTTP.Request, HTTP.Response},
    name::String
)::Union{HTTP.Cookie, Nothing}
```

HTTP.Request または HTTP.Response オブジェクトからクッキーを取得します。

# 引数

  * `payload`: HTTP.Request または HTTP.Response オブジェクト。
  * `name`: クッキーの名前。

# 戻り値

関数はクッキーが存在する場合はそれを返し、存在しない場合は何も返しません。
