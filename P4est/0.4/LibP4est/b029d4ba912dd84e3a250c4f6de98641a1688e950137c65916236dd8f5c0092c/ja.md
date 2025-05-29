```
p4est_lnodes_share_all(node_data, lnodes)
```

[`p4est_lnodes_share_all_end`](@ref) を [`p4est_lnodes_share_all_begin`](@ref) の後に直接呼び出すのと同等です。通信コストをマスクするために行えるローカル作業がない場合に使用します。

### 戻り値

受信したデータを含む完全に初期化されたバッファ。データを処理した後、このバッファは [`p4est_lnodes_buffer_destroy`](@ref) で解放する必要があります。

### プロトタイプ

```c
p4est_lnodes_buffer_t *p4est_lnodes_share_all (sc_array_t * node_data, p4est_lnodes_t * lnodes);
```
