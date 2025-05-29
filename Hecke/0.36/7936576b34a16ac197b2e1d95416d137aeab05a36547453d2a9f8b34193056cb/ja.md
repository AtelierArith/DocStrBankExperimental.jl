```
genus_representatives(L::QuadLat; max = inf, use_auto = true)
                                                    -> Vector{QuadLat}
```

$$
L
$$

の属の同型類の代表を計算します。

最大で`max`の代表が返されます。自己同型の使用は、`use_auto = false`に設定することで無効にできます。
