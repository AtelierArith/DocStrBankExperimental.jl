```
p8est_balance_ext(p8est_, btype, init_fn, replace_fn)
```

2:1 バランスを取ることで、隣接する要素のサイズの違いを調整します。

### パラメータ

  * `p8est`:[in,out] 操作対象の `p8est`。
  * `btype`:[in] バランスタイプ（面、エッジ、またはコーナー/フル）。コーナーバランスは、PDEを離散化する際にはほとんど必要なく、メッシュのグレーディングを滑らかにするだけです。
  * `init_fn`:[in] 自動的に割り当てられた user_data を初期化するためのコールバック関数。
  * `replace_fn`:[in] ユーザーが置き換える四分木に基づいて、受信する四分木を変更できるようにするコールバック関数。

### プロトタイプ

```c
void p8est_balance_ext (p8est_t * p8est, p8est_connect_type_t btype, p8est_init_t init_fn, p8est_replace_t replace_fn);
```
