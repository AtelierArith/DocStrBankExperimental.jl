```
p8est_ghost_expand_by_lnodes(p4est_, lnodes, ghost)
```

ノードサポートを使用して隣接性を定義する代わりに、[`p8est_ghost_expand`](@ref)()と同様にゴーストレイヤーを拡張します。

### パラメータ

  * `p8est`:[in] ゴーストレイヤーが生成されたフォレスト。
  * `lnodes`:[in] サポートするノード。
  * `ghost`:[in,out] 拡張されるゴーストレイヤー。

### プロトタイプ

```c
void p8est_ghost_expand_by_lnodes (p8est_t * p4est, p8est_lnodes_t * lnodes, p8est_ghost_t * ghost);
```
