```
LogBinner([::Type{T}; capacity::Int])
```

`T`型の値を（少なくとも）`capacity`個処理できる`LogBinner`を作成します。

デフォルトは`T = Float64`および`capacity = 2^32-1 ≈ 4e9`です。
