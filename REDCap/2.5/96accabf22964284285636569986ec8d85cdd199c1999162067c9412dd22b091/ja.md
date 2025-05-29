```
function import_user_DAG_assignment(; url=get_url(), token=get_token(), data, format=nothing, returnFormat=nothing,)
```

REDCap APIユーザーの現在のデータアクセスグループ（DAG）を切り替えます

# Named arguments

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン（デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る）
  * `dag`: 意図されたDAGのためのユニークなグループ名
