```
info(lk::Link)
```

`lk`に関連付けられたアクターの状態を返します：

  * 実行可能であれば`Actors.Info`、
  * 完了していれば`:done`、
  * それ以外の場合は失敗したタスクを返します。
