```
p8est_ghost_support_lnodes(p8est_, lnodes, ghost)
```

すべてのノードのサポートを含むようにゴーストレイヤーを拡張します。

### パラメータ

  * `p8est`:[in] ゴーストレイヤーが生成されたフォレスト。
  * `lnodes`:[in] サポートするノード。
  * `ghost`:[in,out] 拡張されるゴーストレイヤー。

### プロトタイプ

```c
void p8est_ghost_support_lnodes (p8est_t * p8est, p8est_lnodes_t * lnodes, p8est_ghost_t * ghost);
```
