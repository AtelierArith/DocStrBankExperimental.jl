```
p8est_lnodes_share_all_begin(node_data, lnodes)
```

[`p8est_lnodes_share_all_begin`](@ref)

*node_data* は任意の型のユーザー定義配列であり、各エントリは一致するインデックスの *lnodes* ローカルノードエントリに関連付けられています。現在のプロセスとエントリを共有するすべてのプロセスに対して、そのプロセスの *node_data* 配列の値が上記のように *buffer*->recv*buffers エントリに書き込まれます。ユーザーは、ノードを共有するすべてのプロセスからのデータを必要とする任意の作業（reduce、max、min など）を実行できます。作業が終了したら、*buffer* は [`p8est*lnodes*buffer*destroy`](@ref) で破棄する必要があります。

*node_data* の値が送信されることは保証されておらず、*buffer*->recv*buffer エントリが受信されることも、[`p8est*lnodes*share*all*begin`](@ref) によって作成された *buffer* が [`p8est*lnodes*share*all_end`](@ref) に渡されるまで保証されません。

### プロトタイプ

```c
p8est_lnodes_buffer_t *p8est_lnodes_share_all_begin (sc_array_t * node_data, p8est_lnodes_t * lnodes);
```
