```
getcollectionpublink(client::PCloudClient; kwargs...)
```

現在のユーザーが所有するコレクションへの公開リンクを生成します。

このメソッドは、getfilepublinkと同じオプションのパラメータを持っています。

*注:* コレクションを指す公開リンクは、ツリーリンクがスナップショットであるのに対し、コレクションのリアルタイム画像であるという利点があります。

出典: https://docs.pcloud.com/methods/public_links/getcollectionpublink.html

# 引数

  * `collectionid::Int`: コレクションのID

# オプションの引数

  * `expire::datetime`: リンクが無効になる日時
  * `maxdownloads::Int`: このフォルダからの最大ダウンロード数（同じファイルでも）。
  * `maxtraffic::Int`: このリンクが消費する最大トラフィック（バイト単位、開始されたダウンロードはこの制限に収まるようにカットされません）
  * `shortlink::Int`: 設定されている場合、短いリンクも生成されます

# 出力例

```
{
    "result": 0,
    "link": "https://my.pcloud.com/#page=publink&code=PUBLIC_LINK_CODE",
    "code": "PUBLIC_LINK_CODE",
    "linkid": LINK_ID
}
```
