```
function export_logging(; url=get_url(), token=get_token(), format=nothing, logtype=nothing, user=nothing, record=nothing, dag=nothing, beginTime=nothing, endTime=nothing,)
```

指定されたイベントにデータ収集機器のマッピングをエクスポートするための長期的なREDCapプロジェクト

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `format`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `logtype`: 出力をイベントタイプに制限するオプション (export, manage, user, record, record*add, record*edit, record*delete, lock*record, page_view)
  * `user`: 特定のユーザーに出力を制限するオプション
  * `record`: 特定のレコードに出力を制限するオプション
  * `dag`: 特定のデータアクセスグループ (DAG) に出力を制限するオプション
  * `beginTime`: 指定された日時以降に記録されたイベントに出力を制限するオプション
  * `endTime`: 指定された日時以前に記録されたイベントに出力を制限するオプション
