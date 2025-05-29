```
setproperty!(plan::RecoPlan{T}, name::Symbol, x::X) where {T, X}
```

`plan`のプロパティ`name`を`x`に設定します。`plan.name = x`と同等です。プロパティに添付されたコールバックをトリガーします。
