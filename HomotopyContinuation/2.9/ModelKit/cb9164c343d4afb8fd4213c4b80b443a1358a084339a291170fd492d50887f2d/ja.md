```
variables(prefix::Union{Symbol,String}, indices...)
```

与えられた `prefix` とインデックスを持つ変数の `Array` を作成します。式 `@var x[1:3, 1:2]` は `x = variables(:x, 1:3, 1:2)` と同等です。
