```
volume(level::Real; instrument::Integer=-1)
```

`instrument`のグローバルボリュームを`level`に設定します `[0.0:db2lin(6)]≈[0.0:2.0]`。デフォルトは現在選択されている楽器です。
