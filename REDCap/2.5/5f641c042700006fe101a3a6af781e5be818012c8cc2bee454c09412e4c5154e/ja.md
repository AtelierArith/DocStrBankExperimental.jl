```
function export_arms(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, arms=nothing,)
```

REDCapプロジェクトの研究アームをエクスポートします

# 注意事項

`arms`に値が提供されていない場合、すべての研究アームが返されます。

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取られます)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取られます)
  * `format`: 希望する出力形式: `:csv`、`:json`、または`:xml` (デフォルト)
  * `arms`: 研究アームの名前 (スカラーまたはベクター可能)
