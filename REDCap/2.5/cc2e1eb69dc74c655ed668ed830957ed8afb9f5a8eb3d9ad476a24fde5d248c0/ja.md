```
function export_file_from_file_repository(; url=get_url(), token=get_token(), doc_id=nothing,
```

ファイルリポジトリからファイルをエクスポートする

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `doc_id`: ファイルのdoc_id
