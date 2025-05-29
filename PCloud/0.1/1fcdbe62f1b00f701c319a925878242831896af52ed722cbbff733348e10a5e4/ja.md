```
collection_move(client::PCloudClient; kwargs...)
```

現在のユーザーが所有する特定のコレクション内のアイテムの位置を変更します。

ソース: https://docs.pcloud.com/methods/collection/collection_move.html

# 引数

  * `collectionid::Int`: コレクションのID。
  * `item::Int`: コレクション内のアイテムの位置。
  * `fileid::Int`: コレクション内で移動するファイルのID。
  * `position::Int`: アイテムを配置する位置。

# 出力例

```
{
    "result": 0
}
```
