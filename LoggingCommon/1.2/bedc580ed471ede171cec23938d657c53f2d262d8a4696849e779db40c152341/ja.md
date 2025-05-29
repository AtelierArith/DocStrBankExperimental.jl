```
validate_log_level(level::Symbol)
```

`level`が知られている名前付きログレベルでない場合、`UnknownLogLevelException`をスローします。それ以外の場合は、`nothing`を返します。
