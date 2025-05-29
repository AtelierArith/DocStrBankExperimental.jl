```
p4est_connectivity_refine(conn, num_per_edge)
```

接続性を均等に細分化します。これは、2の累乗以外のもので均等に細分化したい場合に便利です。

### パラメータ

  * `conn`:[in] 有効な接続性
  * `num_per_edge`:[in] 各方向の新しい木の数。P4EST*OLD*QMAXLEVELビットを超えてはいけません。

### 戻り値

細分化された接続性。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_refine (p4est_connectivity_t * conn, int num_per_edge);
```
