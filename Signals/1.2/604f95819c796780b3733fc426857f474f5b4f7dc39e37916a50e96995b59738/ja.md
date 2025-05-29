```
strict_push!(s::Signal, val, async = Signals.async_mode())
```

`s`を`val`に設定し、派生信号に伝播させます。`async`が`true`（デフォルト）であれば、派生信号への更新は非同期的に行われます。
