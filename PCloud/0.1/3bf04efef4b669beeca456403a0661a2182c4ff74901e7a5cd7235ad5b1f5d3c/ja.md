```
changepublink(client::PCloudClient; kwargs...)
```

指定された公開リンクを変更します

ソース: https://docs.pcloud.com/methods/public_links/changepublink.html

# 引数

  * `linkid::Int`: 変更するリンクのID

# オプション引数

次のオプションパラメータの1つ以上を指定する必要があります:

  * `shortlink::Int`: これを設定すると、リンクの短縮リンクが作成されます。レスポンスにはshortcodeとshortlinkフィールドが含まれます。
  * `deleteshortlink::Int`: これを設定すると、リンクに関連付けられた短縮リンクが削除されます
  * `expire::datetime`: リンクの新しい有効期限を設定します
  * `deleteexpire::datetime`: 設定すると、リンクの有効期限が削除されます（リンクは期限切れになりません）
  * `maxtraffic::Int`: トラフィック制限を変更します。無制限にするには0に設定します
  * `maxdownloads::Int`: ダウンロード制限を変更します。無制限にするには0に設定します

# 出力例

```
{
    result: 0
}
```
