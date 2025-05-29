```
get_session(
    req::HTTP.Request,
    res::HTTP.Response
)::Union{Session, Nothing}
```

HTTP.RequestおよびHTTP.Responseオブジェクトのセッションストレージからセッションを取得します。セッションが存在しない場合は、新しく作成されます。

# 引数

  * `req`: HTTP.Requestオブジェクト。
  * `res`: HTTP.Responseオブジェクト。

# 戻り値

関数は、セッションが存在する場合はそれを返し、存在しない場合は新しく作成されたセッションを返します。
