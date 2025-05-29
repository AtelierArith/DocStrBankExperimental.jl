```
FixedMemoryPwq(len::Int64)
```

固定長の `BoundedQuadratic` のベクターを持つ区分二次関数を表します。

フィールドは次のことを表します：

  * `f_list`: `BoundedQuadratic` 関数の `Vector`
  * `len`: `f_list` のエントリがいくつ埋まっているか。
