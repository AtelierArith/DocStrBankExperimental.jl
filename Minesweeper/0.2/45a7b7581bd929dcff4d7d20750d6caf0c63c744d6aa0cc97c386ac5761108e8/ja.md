```
Cell(;has_mine=false, flagged=false, revealed=false, mine_count=0, idx=(0,0))
```

Cellはマインスイーパーにおけるセルの状態を表します

  * `has_mine`: セルに地雷が含まれている場合はtrue
  * `flagged`: セルが地雷があるとフラグ付けされている場合はtrue
  * `revealed`: セルが明らかにされている場合はtrue
  * `mine_count`: 隣接するセルの地雷の数
  * `idx`: セルのカーテシアンインデックス
