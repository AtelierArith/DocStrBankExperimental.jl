```
function delete_DAGs(; url=get_url(), token=get_token(), dags)
```

ファイルリポジトリに新しいフォルダを作成する

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `name`: 新しいフォルダの名前 (最大150文字)
  * `folder_id`: 意図した親ディレクトリのfolder_id (デフォルトはファイルリポジトリのトップレベルディレクトリ)
  * `dag_id`: オプションでフォルダアクセスをデータアクセスグループに制限
  * `role_id`: オプションでフォルダアクセスをユーザーロールに制限
