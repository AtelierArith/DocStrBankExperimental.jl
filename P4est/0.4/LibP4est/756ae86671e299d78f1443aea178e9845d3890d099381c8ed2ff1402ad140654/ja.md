```
p8est_lnodes_share_owned(node_data, lnodes)
```

[`p8est_lnodes_share_owned_end`](@ref) を [`p8est_lnodes_share_owned_begin`](@ref) の後に直接呼び出すのと同等です。通信コストをマスクするために行えるローカル作業がない場合に使用します。

### プロトタイプ

```c
void p8est_lnodes_share_owned (sc_array_t * node_data, p8est_lnodes_t * lnodes);
```
