```
p8est_lnodes_share_owned_begin(node_data, lnodes)
```

[`p8est_lnodes_share_owned_begin`](@ref)

*node_data* は任意の型のユーザー定義配列であり、各エントリは対応するインデックスの *lnodes* ローカルノードエントリに関連付けられています。現在のプロセス以外のプロセスによって所有されている各ローカルノードエントリについて、所有プロセスの *node_data* 配列の値が現在のプロセスの *node_data* 配列に直接書き込まれます。*node_data* の値は、[`p8est_lnodes_share_owned_begin`](@ref) によって作成された *buffer* が [`p8est_lnodes_share_owned_end`](@ref) に渡されるまで送信または受信されることは保証されません。

メモリ中立であるために、[`p8est_lnodes_share_owned_begin`](@ref) によって作成された *buffer* は [`p8est_lnodes_buffer_destroy`](@ref) で破棄されなければなりません（[`p8est_lnodes_share_owned_end`](@ref) では破棄されません）。

### プロトタイプ

```c
p8est_lnodes_buffer_t *p8est_lnodes_share_owned_begin (sc_array_t * node_data, p8est_lnodes_t * lnodes);
```
