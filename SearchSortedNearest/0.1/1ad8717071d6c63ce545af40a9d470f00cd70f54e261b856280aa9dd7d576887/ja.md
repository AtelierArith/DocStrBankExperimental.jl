```
searchsortednearest(a, x; by=<transform>, lt=<comparison>, distance=(a,b) -> abs(a-b), rev=false)
```

ソートされたコレクション `a` の中で `x` との距離が最も小さいインデックスを見つけます。 競合がある場合は、最小のインデックスが選ばれます。

# 例

```
using SearchSortedNearest

searchsortednearest(1:10, 1.1) == 1
searchsortednearest(1:10, 1.9) == 2
```
