```
p8est_ghost_expand(p8est_, ghost)
```

ゴースト層とミラーのサイズを隣接の追加層分だけ拡張します。

### パラメータ

  * `p8est`:[in] ゴースト層が生成されたフォレスト。
  * `ghost`:[in,out] 拡張されるゴースト層。

### プロトタイプ

```c
void p8est_ghost_expand (p8est_t * p8est, p8est_ghost_t * ghost);
```
