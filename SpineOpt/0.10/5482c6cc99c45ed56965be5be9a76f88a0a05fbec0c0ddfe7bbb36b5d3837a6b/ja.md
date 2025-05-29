```
t_in_t(m; t_short=anything, t_long=anything)
```

モデル `m` における各要素が二つの `TimeSlice` の `Tuple` である `Array` で、二つ目は一つ目を含みます。

# キーワード引数

  * `t_short`: 指定された場合、`t_short` を含む `TimeSlice` の `Array` を返します。
  * `t_long`: 指定された場合、`t_long` に含まれる `TimeSlice` の `Array` を返します。
