```
collection_delete(client::PCloudClient; kwargs...)
```

現在のユーザーが所有する特定のコレクションを削除します。

システムコレクションは削除できません。この場合、エラー `2065` (コレクションが見つかりません。) が発生します。

Source: https://docs.pcloud.com/methods/collection/collection_delete.html

# 引数

  * `collectionid::Int`: コレクションのID。

# 出力例

```
{
    "result": 0
}
```
