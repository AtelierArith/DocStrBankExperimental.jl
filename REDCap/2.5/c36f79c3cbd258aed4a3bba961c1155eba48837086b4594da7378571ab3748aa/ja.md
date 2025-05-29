```
function export_PDF(; url=get_url(), token=get_token(), format=nothing, record=nothing, event=nothing, instrument=nothing, repeat_instance=nothing, allRecords=nothing, compactDisplay=nothing,)
```

データ収集機器のPDFをエクスポート

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取る)
  * `format`: 希望する出力形式: `:csv`, `:json`, または `:xml` (デフォルト)
  * `record`: レコードID (デフォルトはデータなしのPDF)
  * `event`: 縦断的プロジェクトのユニークなイベント名
  * `instrument`: ユニークな機器名
  * `repeat_instance`: 繰り返しの機器/イベントを持つプロジェクトの繰り返しインスタンス番号
  * `allRecords`: 何らかの値が渡された場合、すべてのレコードがエクスポートされる
  * `compactDisplay`: trueの場合、空のフィールドと未選択のオプションを除外 (デフォルトはfalse)
