```
p4est_ghost_expand_by_lnodes(p4est_, lnodes, ghost)
```

ノードサポートを使用して隣接性を定義する代わりに、[`p4est_ghost_expand`](@ref)()のようにゴーストレイヤーを拡張します。

### パラメータ

  * `p4est`:[in] ゴーストレイヤーが生成されたフォレスト。
  * `lnodes`:[in] サポートするノード。
  * `ghost`:[in,out] 拡張されるゴーストレイヤー。

### プロトタイプ

```c
void p4est_ghost_expand_by_lnodes (p4est_t * p4est, p4est_lnodes_t * lnodes, p4est_ghost_t * ghost);
```
