```
p6est_balance(p6est_, btype, init_fn)
```

森をバランスさせます。

### パラメータ

  * `p6est`:[in] 操作対象の `p6est`。
  * `btype`:[in] バランスタイプ（面、コーナー、またはデフォルト、フル）。
  * `init_fn`:[in] 自動的に割り当てられた user_data を初期化するためのコールバック関数。

### プロトタイプ

```c
void p6est_balance (p6est_t * p6est, p8est_connect_type_t btype, p6est_init_t init_fn);
```
