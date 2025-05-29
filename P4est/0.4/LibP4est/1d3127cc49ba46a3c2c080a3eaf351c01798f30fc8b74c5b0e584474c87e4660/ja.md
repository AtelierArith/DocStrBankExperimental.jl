```
p6est_balance_ext(p6est_, btype, max_diff, min_diff, init_fn, replace_fn)
```

2:1 バランスを取ることで、森林内の隣接要素のサイズの違いを調整します。

### パラメータ

  * `p6est`:[in,out] 処理対象の `p6est`。
  * `btype`:[in] バランスタイプ（面またはコーナー/フル）。コーナーバランスは、PDEを離散化する際にはほとんど必要なく、メッシュのグレーディングを滑らかにするだけです。
  * `max_diff`:[in] 水平の細分化レベルと垂直の細分化レベルの最大の違い
  * `min_diff`:[in] 水平の細分化レベルと垂直の細分化レベルの最小の違い
  * `init_fn`:[in] 自動的に割り当てられた user_data を初期化するためのコールバック関数。
  * `replace_fn`:[in] ユーザーが置き換える四分円に基づいて、受信する四分円を変更できるコールバック関数。

### プロトタイプ

```c
void p6est_balance_ext (p6est_t * p6est, p8est_connect_type_t btype, int max_diff, int min_diff, p6est_init_t init_fn, p6est_replace_t replace_fn);
```
