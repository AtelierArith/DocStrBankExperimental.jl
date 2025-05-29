```
isdiscretetime(ds::DynamicalSystem) → true/false
```

`ds` が離散時間で動作している場合は `true` を返し、連続時間である場合は `false` を返します。これは `ds` の型から推測される情報です。
