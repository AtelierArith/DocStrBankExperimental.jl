```
register(datadep::AbstractDataDep)
```

指定された datadep をプログラムでグローバルに利用可能に登録します。これにより `datadep"Name"` が機能します。`register` はモジュールの `__init__` 内で実行する必要があります。
