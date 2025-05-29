```
function generate_next_record_name(; url=get_url(), token=get_token(),)
```

次のレコード名を生成します

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取ります)
  * `token`: REDCap プロジェクトおよびユーザー名に特有の API トークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取ります)
