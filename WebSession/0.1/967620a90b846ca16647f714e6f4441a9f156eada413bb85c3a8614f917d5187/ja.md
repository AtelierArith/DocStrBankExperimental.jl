```
add_session_data(
    key::String,
    value::Union{String, Real}, 
    req::HTTP.Request = Genie.Requests.request(),
    res::HTTP.Response = Genie.Responses.getresponse()
)::Nothing
```

セッションストレージにデータを追加します。

# 引数

  * `key`: 追加するデータのキー。
  * `value`: 追加するデータの値。
  * `req`: HTTP.Requestオブジェクト。
  * `res`: HTTP.Responseオブジェクト。

# 戻り値

この関数は何も返しません。
