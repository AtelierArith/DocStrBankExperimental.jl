```
struct EmissionsEnergy{T} <: EmissionsData{T}

EmissionsEnergy(_, _)
EmissionsEnergy(_)
EmissionsEnergy()
```

キャプチャはなく、プロセス排出は存在しません。`co2_capture`や`emissions`を入力として必要としませんが、提供された場合はそれを受け入れ、無視します。
