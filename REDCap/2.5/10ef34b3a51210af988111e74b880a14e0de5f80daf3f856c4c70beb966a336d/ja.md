```
function delete_arms(; url=get_url(), token=get_token(), arms,)
```

REDCapプロジェクトから研究アームを削除する

# 注意事項

`arms`に値が提供されていない場合、すべての研究アームが返されます。研究アームを削除すると、含まれているレコードとデータも削除されます。

# 名前付き引数

  * `url`: (デフォルトでは`ENV["REDCAP_API_URL"]`から読み取られます)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトでは`ENV["REDCAP_API_TOKEN"]`から読み取られます)
  * `arms`: 研究アームの名前 (スカラーまたはベクターで指定可能)
