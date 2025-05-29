```
GeneralObservableLogger(observable::Function, T, n_steps)
```

システムの定期的にサンプリングされた観察の記録を保持するロガーです。

`observable` は型 `T` のオブジェクトを返し、メソッド `observable(s::System, neighbors; n_threads::Integer)::T` をサポートする必要があります。
