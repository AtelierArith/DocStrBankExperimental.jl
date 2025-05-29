```
p8est_find_higher_bound(array, q, guess)
```

四分木配列において、tq <= q となる最高の位置 tq を見つけます。

### 戻り値

一致する四分木の ID を返すか、array > q または配列が空の場合は -1 を返します。

### プロトタイプ

```c
ssize_t p8est_find_higher_bound (sc_array_t * array, const p8est_quadrant_t * q, size_t guess);
```
