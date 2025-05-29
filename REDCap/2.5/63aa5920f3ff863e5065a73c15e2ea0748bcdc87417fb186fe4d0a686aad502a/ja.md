```
function delete_events(; url=get_url(), token=get_token(), events=nothing,)
```

REDCapプロジェクトからイベントを削除する

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `events`: 一意のイベント名 (スカラーまたはベクター可能)
