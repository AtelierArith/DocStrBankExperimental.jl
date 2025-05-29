```
exit!(lk::Link, reason=:normal)
exit!(name::Symbol, ....)
```

アクター `lk`（または登録されている場合は `name`）に停止するよう指示します。もし [`term`](@ref _ACT) 関数があれば、`reason` を最後の引数としてそれを呼び出します。
