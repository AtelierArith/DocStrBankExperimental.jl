```
function export_instruments(; url=get_url(), token=get_token(), format=nothing,)
```

インストゥルメントのエクスポート (データ入力フォーム)

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCap プロジェクトおよびユーザー名に特有の API トークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `format`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
