remove_events!: IDによるイベントの削除  -`s`: スケジューラ

  * `until`: 実行するまで
  * `f`: 削除関数。デフォルトは完全一致。

関数シグネチャ:

```julia
remove_events!(scheduler, id, f=(x,id)->x.first.id == id)
```
