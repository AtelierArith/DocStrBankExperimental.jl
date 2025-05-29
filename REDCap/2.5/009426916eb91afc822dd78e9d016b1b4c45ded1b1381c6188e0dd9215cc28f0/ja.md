```
function delete_DAGs(; url=get_url(), token=get_token(), dags)
```

REDCapプロジェクトからデータアクセスグループ（DAG）を削除します

# 名前付き引数

  * `url`: （デフォルトで`ENV["REDCAP_API_URL"]`から読み取る）
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン（デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る）
  * `dags`: グループ名（スカラーまたはベクター可能）
