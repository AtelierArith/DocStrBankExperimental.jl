```
get_session_storage(session_id::String)::Union{Session, Nothing}
```

セッションIDに対してセッションストレージからセッションを取得します。

# 引数

  * `session_id`: セッションID。

# 戻り値

関数は、セッションが存在する場合はそのセッションを返し、存在しない場合は何も返しません。
