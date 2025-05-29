```
p8est_connectivity_refine(conn, num_per_edge)
```

接続性を均等に細分化します。これは、2の累乗以外の何かで均等に細分化したい場合に便利です。

### パラメータ

  * `conn`:[in] 有効な接続性
  * `num_per_edge`:[in] 各方向の新しい木の数。P8EST*OLD*QMAXLEVELビットを超えてはなりません。

### 戻り値

細分化された接続性。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_refine (p8est_connectivity_t * conn, int num_per_edge);
```
