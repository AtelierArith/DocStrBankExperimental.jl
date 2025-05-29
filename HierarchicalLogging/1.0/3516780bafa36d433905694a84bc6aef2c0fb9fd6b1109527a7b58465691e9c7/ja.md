```
min_enabled_level!(h::HierarchicalLogger, level; [force], [recurse]) -> LogLevel

`h`のルートロガーのログレベルを`level`に設定します。ルートロガーが`level`未満のメッセージを受信した場合、それらは破棄され、ログに記録されません。

`h`内のすべてのロガーの最小`LogLevel`を返します。
```
