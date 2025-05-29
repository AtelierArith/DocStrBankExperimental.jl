```
start_session(req::HTTP.Request, res::HTTP.Response)::Session
```

HTTP.RequestおよびHTTP.Responseオブジェクトに対してセッションを開始します。セッションがすでに存在するかどうかを確認し、存在する場合はそれを返します。クッキーはレスポンスに設定されます。セッションはセッションストアに追加されます。

# 引数

  * `req`: HTTP.Requestオブジェクト。
  * `res`: HTTP.Responseオブジェクト。

# 戻り値

関数は新しいセッションまたは既存のセッションを返します。
