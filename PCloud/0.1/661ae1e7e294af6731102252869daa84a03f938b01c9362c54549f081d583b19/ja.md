```
trash_clear(client::PCloudClient; kwargs...)
```

ファイルまたはフォルダを`Trash`から*完全に*削除します。

この方法で削除されたファイルやフォルダは復元できません。

`folderid='0'`の場合、`Trash`内のすべてのデータが削除されます。

出典: https://docs.pcloud.com/methods/trash/trash_clear.html

# 引数

  * `fileid::Int`: Trashから削除されるファイルのファイルID
  * `folderid::Int`: Trashから削除されるフォルダのフォルダID

`fileid`または`folderid`を使用します。

# 出力例

```
{
    "result": 0
}
```
