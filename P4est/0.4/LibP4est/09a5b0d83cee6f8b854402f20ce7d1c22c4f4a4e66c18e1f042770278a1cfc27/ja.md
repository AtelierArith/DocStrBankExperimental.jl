```
p4est_balance(p4est_, btype, init_fn)
```

2:1 バランスで隣接する要素のサイズの違いを調整します。

### パラメータ

  * `p4est`:[in,out] 操作対象の `p4est`。
  * `btype`:[in] バランスタイプ（面またはコーナー/フル）。コーナーバランスは、PDEを離散化する際にはほとんど必要ありません; 単にメッシュのグレーディングを滑らかにします。
  * `init_fn`:[in] 自動的に割り当てられた user_data を初期化するためのコールバック関数。

### プロトタイプ

```c
void p4est_balance (p4est_t * p4est, p4est_connect_type_t btype, p4est_init_t init_fn);
```
