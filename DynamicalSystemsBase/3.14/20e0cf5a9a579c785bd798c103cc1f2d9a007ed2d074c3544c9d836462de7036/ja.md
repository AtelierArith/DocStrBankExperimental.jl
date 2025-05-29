```
isdeterministic(ds::DynamicalSystem) → true/false
```

`ds` が決定論的である場合は `true` を返します。すなわち、動的ルールにランダム性が含まれていません。これは `ds` の型から推測される情報です。
