```
p8est_connectivity_permute(conn, perm, is_current_to_new)
```

[`p8est_connectivity_permute`](@ref) 接続 *conn* の木の順列 *perm* を与えられた場合、*conn* の木をその場で順列し、*conn* を一致させる。

### パラメータ

  * `conn`:[in,out] 木が順列される接続。
  * `perm`:[in] 要素が size_t の順列配列。
  * `is_current_to_new`:[in] true の場合、perm の j 番目のエントリは、現在のインデックスが j であるエントリの新しいインデックスであり、そうでない場合、perm の j 番目のエントリは、順列後にインデックスが j になる木の現在のインデックスである。

### プロトタイプ

```c
void p8est_connectivity_permute (p8est_connectivity_t * conn, sc_array_t * perm, int is_current_to_new);
```
