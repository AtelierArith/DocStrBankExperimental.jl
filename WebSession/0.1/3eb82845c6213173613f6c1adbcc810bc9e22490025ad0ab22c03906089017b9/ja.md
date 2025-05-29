```
session_exists(payload::Union{HTTP.Request, HTTP.Response})::Bool
```

HTTP.Request または HTTP.Response オブジェクトのセッションが存在するかどうかを確認します。

# 引数

  * `payload`: HTTP.Request または HTTP.Response オブジェクト。

# 戻り値

セッションが存在する場合は true を返し、存在しない場合は false を返します。
