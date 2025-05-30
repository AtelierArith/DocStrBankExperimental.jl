```
t8_forest_partition_next_nonempty_rank(forest, rank)
```

`t8*forest*partition*create*offsets`がすでに呼び出されている場合、与えられたランクに対して次の空でない大きなランクを計算します。

# 引数

  * `forest`:[in] 森。
  * `rank`:[in] MPIランク。

# 戻り値

ランク q > *rank* であり、森に *q* の要素がある。もしそのような *q* が存在しない場合、mpisizeを返します。

### プロトタイプ

```c
int t8_forest_partition_next_nonempty_rank (t8_forest_t forest, int rank);
```
