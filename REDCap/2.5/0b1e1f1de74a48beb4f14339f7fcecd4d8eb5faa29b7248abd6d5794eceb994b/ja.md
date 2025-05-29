```
function delete_file(; url=get_url(), token=get_token(), returnFormat=nothing, record=nothing, field=nothing, event=nothing, repeat_instance=nothing,)
```

REDCapプロジェクトのレコードからファイルを削除します

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `returnFormat`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `record`: レコードID
  * `field`: ファイルを含むフィールドの名前
  * `event`: ユニークなイベント名 (縦断的プロジェクト)
  * `repeat_instance`: 繰り返しイベントまたはインストゥルメントのインスタンス番号 (該当する場合、デフォルトは1)
