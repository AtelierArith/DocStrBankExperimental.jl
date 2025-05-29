```
solve!( problem :: Problem; verbose=true )
```

初期値問題を解く（すなわち、時間的に統合する）

引数 `problem` は `Problem` 型である必要があります。これは、例えば `Problem(model, initial, param)` によって構築できます。

キーワード引数 `verbose = false` の場合、情報は印刷されません（デフォルトは `true` です）。
