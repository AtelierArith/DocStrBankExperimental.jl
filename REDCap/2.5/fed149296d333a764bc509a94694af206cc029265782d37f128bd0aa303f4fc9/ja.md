```
function rename_record(; url=get_url(), token=get_token(), record, new_record_name, arm=nothing,)
```

レコードの名前を変更する

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCap プロジェクトおよびユーザー名に特有の API トークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `record`: 現在のレコード名
  * `new_record_name`: 新しいレコード名
  * `arm`: オプションでこのアーム番号に名前変更を制限する
