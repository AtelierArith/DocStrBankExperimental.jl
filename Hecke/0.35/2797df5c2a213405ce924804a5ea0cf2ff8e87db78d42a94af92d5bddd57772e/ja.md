```
genus_representatives(L::HermLat; max = inf, use_auto = true,
                                             use_mass = false)
                                                      -> Vector{HermLat}
```

与えられたエルミート格子 `L` の属の同型類の代表を返します。最大で `max` 個の代表が返されます。

`L` が定義されている場合、`L` の自己同型群の使用はデフォルトで有効です。`use_auto = false` によって無効にすることができます。`L` が非定義の場合、`use_auto` のエントリは効果がありません。質量の計算は `use_mass = true` によって有効にすることができます。
