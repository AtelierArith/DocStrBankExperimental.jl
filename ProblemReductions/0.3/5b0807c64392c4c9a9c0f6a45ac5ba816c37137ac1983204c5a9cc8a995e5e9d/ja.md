```
onehotv(::Type{<:StaticElementVector}, i, v)
onehotv(::Type{<:StaticBitVector}, i)
```

指定された位置 `i` に値 `v`（指定されていない場合は 1）を持つ静的要素ベクトルを返します。
