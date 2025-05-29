```
p4est_ghost_support_lnodes(p4est_, lnodes, ghost)
```

ゴースト層を拡張して、ローカルパーティションでサポートされているすべてのノードのサポートを含めます。

### パラメータ

  * `p4est`:[in] ゴースト層が生成されたフォレスト。
  * `lnodes`:[in] サポートするノード。
  * `ghost`:[in,out] 拡張されるゴースト層。

### プロトタイプ

```c
void p4est_ghost_support_lnodes (p4est_t * p4est, p4est_lnodes_t * lnodes, p4est_ghost_t * ghost);
```
