```
t_in_t_excl(m; t_short=anything, t_long=anything)
```

[t*in*t](@ref)と同様ですが、同じ`TimeSlice`のタプルを除外します。

# キーワード引数

  * `t_short`: 指定された場合、`t_short`（`t_short`自体を除く）を含む`TimeSlice`の`Array`を返します。
  * `t_long`: 指定された場合、`t_long`（`t_long`自体を除く）に含まれる`TimeSlice`の`Array`を返します。
