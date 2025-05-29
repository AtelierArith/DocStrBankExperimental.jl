```
get_session_id(req::HTTP.Request, res::HTTP.Response)::Union{String, Nothing}
```

HTTP.Request または HTTP.Response オブジェクトからセッション ID を取得します。最初に HTTP.Request オブジェクトからセッション ID を取得しようとします。存在しない場合は、HTTP.Response オブジェクトから取得しようとします。

# 引数

  * `req`: HTTP.Request オブジェクト。
  * `res`: HTTP.Response オブジェクト。

# 戻り値

関数はセッション ID が存在する場合はそれを返し、存在しない場合は何も返しません。
