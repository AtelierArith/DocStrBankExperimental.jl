```
min_enabled_level!(h::HierarchicalLogger, key, level; [force=true], [recurse=true]) -> LogLevel
```

`h`に関連付けられたロガー`L`のレベルを再帰的に設定します。

`haskey(h, key)`が真であれば、`L`のログレベルを`level`に設定します（`recurse == true`の場合は、そのすべての子のレベルも）。もし`L`の現在のログレベルが`level`より大きい場合、`force == false`であればこのメソッドは既存のレベルを変更しません。

`haskey(h, key) == false`の場合、`key`にロガーが追加されます（ベースロガーは`underlying_logger(closest_logger(h, key))`です）。

`key`に関連付けられた新しい`LogLevel`を返します。
