```
metapropfixed(mp; weights = :default)
```

デフォルトで使用される逆分散法。

`weights`:

  * `:iv` | `:default` (逆分散)
  * `:mh` (マンテル・ヘンゼル)

リスク差については、`Sato, Greenland, & Robins (1989)` の分散推定の修正が使用されます。

*RRおよびORの結果は対数スケールです。**
