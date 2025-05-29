```
select(path::String, cols...; nworkers = 1) => LineIndex
```

  * `path`: JSONLinesファイルへのパス
  * `cols...`: 選択する列名
  * キーワード引数:

      * `nworkers=1`: 結果のLineIndexに対する操作に使用するスレッドの数
