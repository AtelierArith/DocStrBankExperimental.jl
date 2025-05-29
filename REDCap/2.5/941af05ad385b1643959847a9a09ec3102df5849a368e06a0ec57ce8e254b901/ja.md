```
function delete_records(; url=get_url(), token=get_token(), records, arm=nothing, instrument=nothing, event=nothing, repeat_instance=nothing,)
```

REDCapプロジェクトからレコードを削除します

# 名前付き引数

  * `url`: (デフォルトでは `ENV["REDCAP_API_URL"]` から読み取ります)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトでは `ENV["REDCAP_API_TOKEN"]` から読み取ります)
  * `records`: レコード名 (スカラーまたはベクター可能)
  * `arm`: このアーム番号に削除を制限するオプション
  * `instrument`: このユニークなインスツルメント名に削除を制限するオプション
  * `event`: このユニークなイベント名に削除を制限するオプション (縦断的プロジェクトには必須、それ以外は利用不可)
  * `repeat_instance`: この繰り返しインスツルメントまたはイベントに削除を制限するオプション
  * `delete_logging`: trueの場合、削除されたレコードのログ活動を削除します (デフォルトはfalse)
