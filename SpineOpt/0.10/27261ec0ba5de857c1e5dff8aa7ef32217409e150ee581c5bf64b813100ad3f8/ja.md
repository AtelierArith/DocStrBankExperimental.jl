```
t_before_t(m; t_before=anything, t_after=anything)
```

モデル `m` における各要素が2つの *連続した* `TimeSlice` の `Tuple` である `Array`。すなわち、最初の `TimeSlice` が終了する時に2番目が始まる。

# 引数

  * `t_before`: 指定された場合、`t_before` が終了する時に始まる `TimeSlice` の `Array` を返す。
  * `t_after`: 指定された場合、`t_after` が始まる時に終了する `TimeSlice` の `Array` を返す。
