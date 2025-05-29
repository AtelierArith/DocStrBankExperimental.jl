```
p4est_connectivity_permute(conn, perm, is_current_to_new)
```

[`p4est_connectivity_permute`](@ref) 接続 *conn* の木の順列 *perm* に基づいて、*conn* の木をその場で順列し、*conn* を更新して一致させます。

### パラメータ

  * `conn`:[in,out] 木が順列される接続。
  * `perm`:[in] 要素が size_t の順列配列。
  * `is_current_to_new`:[in] true の場合、perm の j 番目のエントリは、現在のインデックスが j であるエントリの新しいインデックスです。そうでない場合、perm の j 番目のエントリは、順列後にインデックスが j になる木の現在のインデックスです。

### プロトタイプ

```c
void p4est_connectivity_permute (p4est_connectivity_t * conn, sc_array_t * perm, int is_current_to_new);
```
