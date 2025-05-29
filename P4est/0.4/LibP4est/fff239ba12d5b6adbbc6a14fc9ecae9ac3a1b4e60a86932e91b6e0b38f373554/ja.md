```
p4est_ghost_expand(p4est_, ghost)
```

ゴースト層とミラーのサイズを隣接の追加層によって1層拡張します。

### パラメータ

  * `p4est`:[in] ゴースト層が生成されたフォレスト。
  * `ghost`:[in,out] 拡張されるゴースト層。

### プロトタイプ

```c
void p4est_ghost_expand (p4est_t * p4est, p4est_ghost_t * ghost);
```
